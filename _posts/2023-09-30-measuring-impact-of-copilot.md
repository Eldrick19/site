---
title: "Measuring the Impact of GitHub Copilot"
categories:
- GitHub
---

How can I measure the effectiveness of GitHub Copilot for my Enterprise?
========================================================================

GitHub Copilot is a great tool that can be used to improve the productivity of developers, and with GitHub experimenting with new ways of boosting productivity and developer experience through AI, it is likely that Copilot will be used more and more in the future.

However, as with any tool you are purchasing for your business, it is important to measure its effectiveness before fully committing. You are after all paying for every person your company decides to assign it to. To do this, you need to have a clear understanding of what Copilot is doing for your developers. And before that, it is important to clarify what a developer does.

What is a Developer?
--------------------

According to the [US Bureau of Labor Statistics](https://www.bls.gov/ooh/computer-and-information-technology/software-developers.htm), a software developer is someone who "designs, develops, and tests computer software". We know that this definition is not complete, as the term "software developer" encompasses a wide range of people across industries that tinker with code. However, in an Enterprise context, we can summarize it as:

A software developer is someone who designs software solutions to solve business problems.

Most of the time, the software solution is then implemented by writing code. Because the role involves a level of design, it is not uncommon for developers to spend a significant amount of time thinking about the solution before writing any code. This is especially true for senior developers, who will be designing more complex or higher impact solutions to equally complex or high impact business problems. To grossly oversimplify, we can break down the role of a developer into two parts:

-   Designing a solution to a business problem

-   Implementing the solution by writing code

But this is not a linear process. It's more so cyclical, where as a developer, I will go back and forth between the two parts until the solution is fully implemented.

For example, I may find that the code I am writing is not as optimal and redesign it on the fly. This can happen at team scope as well, where a change I have designed and implemented is pushed into Production, and is then redesigned and reimplemented by myself or another team member. This cyclical loop can happen in a second (e.g. changing an object type in my editor), over months (e.g. changing the architecture of a system through an initiative), and anything in between.

As with any work that involves a level of design, there is a level of subjectivity. Development can sometimes be closer to an art than a science. Development is a very nonlinear process.

How are you measuring the effectiveness of your Developer teams?
----------------------------------------------------------------

The cyclical nature of development means that measuring effectiveness will differ widely based on your goals, be it shorter time to market, higher quality products, reduced risk, or something else. But the one thing that is usually consistent in what businesses are looking for is Velocity. Your business is likely looking at a metric like "number of story points per sprint", or "deployment frequency". These are very important metrics that give you the health of your DevOps practice, but it's worth zooming out a bit to ask ourselves why we measure these things in the first place.

### Developer Velocity vs Developer Productivity

Something we talk a lot about at GitHub and Microsoft is "[Developer Velocity](https://azure.microsoft.com/en-us/solutions/developer-velocity)", which is the ability for an organization to empower developers, create the environment for them to innovate, and remove points of friction. Developer velocity goes beyond just measuring speed, but also encompasses the ability to unleash the full potential of development talent. There are broadly 3 key components to it:

1.  Best-in-class tools

2.  Better working practices

3.  An aligned culture

Examples of Developer Velocity initiatives include eliminating redundant meetings, creating a culture of security, or leveraging tools that promote collaboration. You can think of Developer Velocity as the ability for a team to ship better code, and innovate, faster. It directly impacts business outcomes.

Developer Productivity, on the other hand, focuses on the individual developer, and how well they are able to accomplish specific tasks - i.e. a single loop of the design/implement cycle mentioned earlier. Certain working practices (pair programming, TDD) can improve my Productivity, and so can tools.

A great analogy for Developer Velocity is [rowboat team](https://colinsalmcorner.com/scaling-dev-sec-ops/#team-autonomy-vs-enterprise-alignment) - where our goal is to have the team reach their destination healthily and fast. If we spend all our time training the first rower, they will become more powerful over time, but we might find that when it comes to game day, another rower is much slower than we thought - they had an injury we should have caught earlier. We improved one metric (the first rower's power), but missed another component of the team that affected our performance.

Developer Productivity is one of the important nodes of Velocity, just as the first rower is to a successful rowboat race, but it is not the only thing that impacts it.

![Developer Velocity](/assets/blog/2023-09-30-measuring-impact-of-copilot/developer-velocity.png)

How do I measure the effectiveness of Copilot?
----------------------------------------------

GitHub Copilot is a Developer Productivity tool. It is intended to help developers go through the development loop faster by aiding both the design and implementation processes. By being able to spend less time thinking about how to implement a solution, developers can spend more time designing the optimal solution. And they can then accelerate that design process through [chat interactions with Copilot](https://github.blog/2023-07-20-github-copilot-chat-beta-now-available-for-every-organization/).

GitHub Copilot will impact your overall Developer Velocity strategy, but it is not the only thing that will impact it, so it could be misleading to only look at Developer Velocity metrics. Instead, we'll focus on Developer Productivity metrics as much as possible.

There are two ways to measure the effectiveness of Copilot on Productivity, and this can apply to generative AI productivity tools in general: Quantitative and Qualitative. Quantitative measures are the answer to the question you're probably asking about Copilot, the hard numbers, "Does this help us accomplish our tasks faster?". Qualitative measures are more subjective, and will involve asking developer teams directly about their experience.

#### 1\. Quantitative Data - Leveraging the measurements that have been collected for you

The reality of generative AI productivity gains is that it is hard to measure. Whether it is to generate code like GitHub Copilot, or meeting notes like Microsoft 365 Copilot, generative AI helps cyclical processes, which as we established are fluid. For example, how much more effective is a developer with or without access to Stack Overflow? What about searching the internet in general? We know there are gains (I would be severely limited in development without access to the internet!), but it's not something you can measure as simply as "time from commit to deployment". Copilot helps in a similar, informal way.

Save running a scientific study and having 2 groups work on the exact same work with and without Copilot, getting precise measures on the impact to Developer Productivity will not be straightforward. Luckily, we have done that work for you! [In our own study](https://github.blog/2022-09-07-research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/), we found that developers using Copilot were up to 55% faster than those that didn't. [There are other studies as well that show similar results](https://www.mckinsey.com/capabilities/mckinsey-digital/our-insights/unleashing-developer-productivity-with-generative-ai). These studies are available in part because we don't expect you as an organization to spend time measuring individual task speed.

We also realize supplemental data on usage and acceptance rate help paint a better picture. This is why the GitHub Copilot team is working on providing this information to you in the future.

#### 2\. Quantitative Data - Leveraging the data you already have

Despite this, you might still want to have some measures of your own. Are you already measuring any metric related to Developer Velocity? You can potentially use these as supplemental data. A great example is "User stories completed per sprint". Other examples include:

-   Cycle Time: Time taken to complete a single user story

-   WIP Items: Number of stories worked on at a specific time

-   Average Test Coverage: If a use case you are evaluating is writing unit tests with Copilot, this is a valid measure

These will not, by themselves, accurately measure the impact of Copilot but can be used alongside previously mentioned and upcoming information.

If you are not tracking any Developer Velocity metrics today, although important, it's worth considering the cost of implementing a tracking of these metrics to simply measure the effectiveness of a tool, where evaluation has already been done. But this is where Qualitative measures come in.

#### 3\. Qualitative Data - Leveraging your developers

Although we want hard data as much as possible personalized to us, we have seen that with generative AI, getting this data isn't simple. Qualitative information is much easier to obtain, and can be just even more valuable. All you really have to do is ask developers how they feel about Copilot!

As part of our GitHub Copilot study mentioned earlier, we emphasized the importance of getting qualitative feedback from developers. On top of actually measuring task speed improvements, we got insight from developers via survey:

![Developer Survey](/assets/blog/2023-09-30-measuring-impact-of-copilot/developer-survey.png)

These questions are based on the [SPACE framework](https://queue.acm.org/detail.cfm?id=3454124), which is a framework we use at GitHub to think about Developer Productivity. SPACE (Satisfaction and well-being, Performance, Activity, Communication and collaboration, and Efficiency and flow) shows us that how developers feel about development has a high correlation with their productivity.

This is why organizations are investing into [Developer Experience (DX) teams](https://github.blog/2023-06-08-developer-experience-what-is-it-and-why-should-you-care/#:~:text=DevEx%20refers%20to%20the%20systems,%2C%20satisfaction%2C%20and%20operational%20impact.): Happier developers are more productive developers.

![SPACE Framework](/assets/blog/2023-09-30-measuring-impact-of-copilot/space-framework.png)



The SPACE framework is an extremely valuable way of operating, as it provides metrics that are easier to measure, and relate to the effectiveness question we are asking ourselves. 

On top of metrics you are already tracking for Velocity, developing a detailed survey for your developers throughout the Copilot adoption process will help gain an understanding of how effective the tool actually is. Here is a sample survey to get started:

![Copilot Questions](/assets/blog/2023-09-30-measuring-impact-of-copilot/copilot-questions.png)

#### 4\. Qualitative Data - Shifting surveys left

Readers involved in application security might be familiar with the reference to shifting left, which really just means bringing security closer to development teams. To really get the most out of developer feedback, you can embrace the shifting left of these surveys through tools like our [Survey Engine](https://github.com/mageroni/copilot-survey-engine) that prompts developers for Copilot feedback right at their pull request. By getting opinions when experiences are fresh in developers minds and they have just exited "the flow", you can get more raw feedback.

Today, there is a high degree of trust you put in professional development teams to intimately design and implement the software that is a crucial part of your business. To provide a generative AI productivity tool to these teams, that same level of trust is required - and that means weighing their feedback as early as possible.

Conclusion
----------

Measuring the effectiveness of GitHub Copilot will be along quantitative and/or qualitative lines. You should focus on qualitative metrics, which are much easier to gather, especially if you don't currently track detailed Developer Velocity metrics. Asking developers how much more empowered using generative AI tools will help determine effectiveness. You can then supplement this with any hard data you are able to gather, with the knowledge that experiments have already been run to demonstrate these tools' effectiveness.