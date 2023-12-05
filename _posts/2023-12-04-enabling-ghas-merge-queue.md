---
title: "Enabling GitHub Advanced Security as a required check with a GitHub Merge Queue"
categories:
- GitHub
- Tutorial
---

If you're looking to enable GitHub Advanced Security in one of your critical repos where you have Merge Queue enabled, this quick post is for you.

At the time of writing this blog, making your GitHub Advanced Security checks "required" in a repository where Merge Queue is enabled will break your merge queue.

If you are already familiar with the issue and just want a quick solution, use this GitHub Action in your workflows to unblock: [code-scanning-status-checker](https://github.com/Eldrick19/code-scanning-status-checker)

If you want to learn more about why this exists, or would like to implement the solution in your organization yourself, you can read on.

What's the problem?
===================

When GitHub Advanced Security's CodeQL scan runs on a pull request, it runs the analysis (by default this is a job in GitHub Actions called "Analyze") and then outputs the results of the analysis to GitHub. This output is, by default, called "Code scanning results / CodeQL". This is the output that you would normally make a required status check.

![Required CodeQl Check]({{ site.baseurl }}/assets/blog/2023-12-04-enabling-ghas-merge-queue/codeql-required-check.png)

Doing this, however, within the context of a merge queue will cause this check to be required in the merge queue. However, the output is never uploaded to the merge queue, making it an expected check that is never completed.

![Merge Queue Stagnant]({{ site.baseurl }}/assets/blog/2023-12-04-enabling-ghas-merge-queue/merge-queue-stagnant.png)

The fact that the output of "Code scanning results" is never uploaded could be considered a bug. At the time of writing this, this is being worked on by GitHub, however there are no timelines. This is a workaround until then

![Problem Diagram]({{ site.baseurl }}/assets/blog/2023-12-04-enabling-ghas-merge-queue/problem-diagram.png)

[Chatter online about it](https://github.com/orgs/community/discussions/46757#discussioncomment-4934046).

Solution
========

To do this, we're going to change the "Code scanning results" check to a GitHub Actions job, rather than the special "GitHub Advanced Security" type check that it is. We'll create a dummy job called "Check CodeQL Status". This job will just check the output of the "Code scanning results" check, and pass or fail based on these results. Let's implement this job step by step

1) First, let's initialize the job and give it the required permissions:

````yaml
check_codeql_status:
    name: Check CodeQL Status
    needs: analyze
    permissions: 
      contents: read
      checks: read
      pull-requests: read
    runs-on: ubuntu-latest
````

2) I'm using the gh CLI to make this query. You could use another method. Note that if you are using self-hosted runners you might need to install the gh CLI before this step (or on your runners in general)

````yaml
- name: Authenticate gh CLI
        run: |
          gh auth login --with-token <<< "${{ secrets.GITHUB_TOKEN }}"
````

3) This step is important. We'll use the GraphQL query to check status of "Code scanning results". The value you enter for the engine will depend here, but I'm using the CodeQL engine, and that's the scan results I want to make mandatory

````yaml
- name: Check CodeQL status
        run: |
          response=$(gh api graphql -f query='
            {
                repository(owner: "${{ github.event.repository.owner.login }}", name: "${{ github.event.repository.name }}") {
                pullRequest(number: ${{ github.event.pull_request.number }}) {
                  commits(last: 1) {
                    nodes {
                      commit {
                        checkSuites(first: 1, filterBy: {checkName: "CodeQL"}) {
                          nodes {
                            checkRuns(first: 1) {
                              nodes {
                                name
                                status
                                conclusion
                              }
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            }
          ')
          conclusion=$(echo $response | jq -r '.data.repository.pullRequest.commits.nodes[0].commit.checkSuites.nodes[0].checkRuns.nodes[0].conclusion')
          if [ "$conclusion" != "SUCCESS" ]; then
            echo "CodeQL check failed"
            exit 1
          fi
````

4) The final, most important, step is to make the job just run at the PR. You don't want this job to run in a merge group as it will fail (it won't find a PR to poll reliably since merge queue uses temporary PRs, and it won't have the underlying "Code scanning results" available to it). To do this I'm adding an if statement to this job (prior to it running)

````yaml
if: $( github.event_name == 'pull_request' )
````

[You workflow should look like this](https://gist.github.com/Eldrick19/629b5d5ffd295e329d36a3606a8a809c)

Here is basically what we're doing:

![Solution Diagram]({{ site.baseurl }}/assets/blog/2023-12-04-enabling-ghas-merge-queue/solution-diagram.png)

Wrapping it up
==============

You can implement this however you're comfortable, copy the job/workflow above, or use the [code-scanning-status-checker](https://github.com/Eldrick19/code-scanning-status-checker) if you don't want to think about it.

As you can see, this solution works only if you want your required check to be at the pull request. This will not be a full solution if you need the required check to be run at both the pull request and in the merge group.

Hope this helps unblock if you're using both Advanced Security and Merge Queue. I will update this post once a fix is productized.