# Agentic AI

1. [Module 1](#1)
    1. [Intro](#2)
    2. [Degrees of autonomy](#3)
    3. [Benefits of Agentic AI](#4)
    4. [Types of applications we can build with Agentic workflows](#5)
    5. [Task decomposition: identifying the steps in a workflow](#6)
    6. [Evaluating Agentic AI (evals)](#7)
    7. [Agentic design patterns](#8)
2. [Module 2 - Reflection pattern](#9)
    1. [Intro](#10)
    2. [Why not just direct generation (Zero-shot prompting)?](#11)

- This course is on the **Best practices to build Agentic AI application.**
- **Driving a disciplined development process, specifically one focused on evals and error analysis,** is the main skill that distinguishes between really good engineers rather than people only talking about Agentic AI. 

<a name="1"></a>
# Module 1

<a name="2"></a>
## Intro

 The four key agentic design patterns:

- Reflection, in which an agent examines its own output and figures out how to improve it
- Tool use, in which an LLM-driven application decides which functions to call to carry out web search, access calendars, send email, write code, etc. 
- Planning, where you’ll use an LLM to decide how to break down a task into sub-tasks for execution, and
- Multi-agent collaboration, in which you build multiple specialized agents — much like how a company might hire multiple employees — to perform a complex task.

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/4_key_agentic_design_patterns.png) 

Source: The Batch newsletter from DeepLearning.ai

Having worked with many teams on many agents, I’ve found that the single biggest predictor of whether someone can build effectively is whether they know how to drive a disciplined process for evals and error analysis. Teams that don’t know how to do this can spend months tweaking agents with little progress to show for it. I’ve seen teams that spent months tuning prompts, building tools for an agent to use, etc., only to hit a performance ceiling they could not break through

But if you understand how to put in evals and how to monitor an agent’s actions at each step (traces) to see when part of its workflow is breaking, you’ll be able to efficiently home in on which components to focus on improving. Instead of guessing what to work on, you'll let evals data guide you. 


- An agentic AI workflow is a process where an LLM-based app executes multiple steps to complete a task
- Agentic workflow can take longer, but it provides better results

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/1.agentic_vs_non_agentic_2.png)

- The most important skill in this domain: taking a complex task and breaking it down into smaller steps for the agentic workflow to execute one step at a time to get the output we want. Knowing how to decompose a task into steps and how to build a component to execute each step well is a tricky but very important skill. For example, back to the essay writing example, we can get an LLM to write an essay outline on topic X, then we can ask another LLM to see if it needs any web search, then another LLM for writing a first draft, another LLM can be asked to see if there is any parts that need revision or more research, in this step we may want to request a human review too, and finally another LLM can revise the draft. So the important skill is to decompose a complex task and get different LLMs to execute each step to get the desired response. 

- We build a research agent

<a name="3"></a>
## Degrees of autonomy
Agents can be autonomous to different degrees:

- Some agents can be less autonomous with a fully deterministic sequence of steps
- In a more autonomous workflow, we let **LLM decides** if it needs to do a web search or use different tools

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/2.degrees_of_autonomy.png)

There is a spectrum:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/3.autonomy_spectrum.png)

<a name="4"></a>
## Benefits of Agentic AI

- Much better performance: The LLM with and withour agentic workflow's capability to write code is compared below:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/coding_benchmark.png)

As shown above, wtapping GPT-3.5 within an agentic workflow can dramatically imporve its performance to write a computer program. In this case, different agentic techniques will be learbed in this course, which can be used to promot GPT-3.5 to write code and maybe reflect on the written code and figure out how to imporve it. This gives GPT-3.5 a much higher level of performance. Similarly, GPT-4 performance can also be dramatically improved in bagentic systems.

Interestingly, the improvement through incorporating agenting workflow is much larger than the improvement from one LLM model generation to the next. 

- Another benefit of agentic workflows is that they can parallelize some tasks and so get them done much faster.

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/parallelization_for_speed.png)

- Another benefit is modularity, like the capability to add or swap out components. This lets me combine the best of different components from many different places to build effective workflow. 

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/modularity.png)

<a name="5"></a>
## Types of applications we can build with Agentic workflows

Here are some examples:
- Invoice processing workflows
- Customer service agents (may require multiple API calls to the database)
- Visual computer use

When there is a clear process to follow it is easier for the agentic workflow to follow steps. If the required steps are not known ahead of time that would be more challenging for agentic workflows. Here is a good summary:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/agentic_AI_suites_for.png)

<a name="6"></a>
## Task decomposition: identifying the steps in a workflow

Identifying the discrete steps forming the whole process is a key to build an agentic workflows. For each individual discrete step, I need to understand to complete this task which AI model or tool I can use to complete this step. If I cannot find any model or tool, I ask myself how I as a human can do this step through decomposing it further down to even smaller steps that then maybe they can be done with models or tools that I have. 

One example of decomposing a task is shown below:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/extracting_info_from_invoice.png)

And here is a summary of the building blocks I have to build an agentic workflow:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/building_blocks.png)

<a name="7"></a>
## Evaluating Agentic AI (evals)

Having a disciplined eval process is a big differentiator between a great engineer and an inefficient one to build agentic workflows. 

Tips: Rather than having evals in advance, just look at the output and identify or look for things that you wish were better. For example, if the competitor name is repeatedly mentioned in the response like shown below:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/low_quality_output.png)

So the best practice is to first build an agentic workflow, then examine the output to see the areas for improvement. 

For the above error we can do below:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/evals.png)

But because LLM outputs free text, it would sometimes be harder to do the evaluation like above. In this case, we can have LLM as a judge as a common technique to evaluate the output:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/llm_as_judge.png)

LLMs are not that good at these 1 to 5 scale ratings, in a later module in the course we will discuss a better technique for this. 

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/evaluating_agentic_ai.png)

<a name="8"></a>
## Agentic design patterns

We saw how to decompose a task into smaller steps, here, we want to kind of combine these building blocks to complete the task. 

Major agentic design patterns:
- Reflection
- Tool use
- Planning
- Multi-agentic workflows

### Reflection

It is a common design pattern where we ask LLM to examine its own outputs or maybe bringing some external sources of information like running the code and see if it generates any error messages and use that as feedback to iterate again and come up with a better version of itw own output. It is not a magic pattern to work 100% of the time but it could lead to a nice bump in the system performance. 

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/reflection.png)

## Tool use

This is just a function calling by LLM:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/tool_use_2.png)

## Planning

The model automatically decised and creates a sequence of actions which may require different API calls. Rather than the developer hard coding the sequence of steps in advance, LLM decides what the steps to take are. Agents that plan today are harder to control and somehow more experimental but sometimes they can give really delightful results. 

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/planning.png)

## Multi-agentic workflows

Just like a human manager who hires a number of others to work together on a complex project in some cases it might make sense for you to hire a set of multiple agents each of which specializes in different roles and have them work together to accomplish a complex task

<a name="9"></a>
# Module 2 - Reflection pattern  

<a name="10"></a>
## Intro

This design pattern is easy to implement. Just like us as humans, we reflect on what we produce LLMs can do the same. We may have an LLM write a first draft of an email and then ask a second LLM probably or the same model to critique the first draft and reflect on it. Or maybe we can get

Different LLMs have different strengths, e.g., reasoning models (also called thinking models) are very good at finding bugs. And so when we ask one LLM to write a first version of code then maybe we can ask a second LLM which is preferably reasoning model to critique the version 1 and identify any potential bugs. We also can execute the code and then feed the second LLM with the observed error message, this would be very useful info for the LLM to improve the first version. 

The reflection design pattern is not magic, and it may or may not lead to a small bump in performance. One design consideration is that reflection is much more powerful if we can inject new, additional external information into the reflection process. For example, if we can run the code and have the error message as additional information in the reflection process, that would be very useful. **So keep in mind when you want to go with this design pattern, think of all the opportunities to inject additional external information into the reflection process.** 

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/reflection_with_external_feedback.png)

<a name="11"></a>
## Why not just direct generation (Zero-shot prompting)? 

This direct generation is also called Zero-shot prompting. 



Some notes:
- Sometimes, reasoning models are better for reflection rather than the non-reasoning models
- 

Evaluating the impact of reflection 



Reference: https://www.deeplearning.ai/courses/agentic-ai/?utm_campaign=Short%20Course%20Announcements&utm_medium=email&_hsenc=p2ANqtz-96j0nIG5ukADk--vE0_v8FrNwu6KCV7SaUd1_Cyb0F6J5dPRBMX5B5bz7Bbulmld3CUaJ4DRpQB3cNV_rhKFdVNUJrWw&_hsmi=384075443&utm_content=384075443&utm_source=hs_email
