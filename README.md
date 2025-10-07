# Agentic AI

1. [Intro](#1)
2. [Degrees of autonomy](#2)
3. 

- This course is on the **Best practices to build Agentic AI application.**
- **Driving a disciplined development process, specifically one focused on evals and error analysis,** is the main skill that distinguishes between really good engineers rather than people only talking about Agentic AI. 

## Intro

- An agentic AI workflow is a process where an LLM-based app executes multiple steps to complete a task
- Agentic workflow can take longer, but it provides better results

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/1.agentic_vs_non_agentic_2.png)

- The most important skill in this domain: taking a complex task and breaking it down into smaller steps for the agentic workflow to execute one step at a time to get the output we want. Knowing how to decompose a task into steps and how to build a component to execute each step well is a tricky but very important skill. For example, back to the essay writing example, we can get an LLM to write an essay outline on topic X, then we can ask another LLM to see if it needs any web search, then another LLM for writing a first draft, another LLM can be asked to see if there is any parts that need revision or more research, in this step we may want to request a human review too, and finally another LLM can revise the draft. So the important skill is to decompose a complex task and get different LLMs to execute each step to get the desired response. 

- We build a research agent

## Degrees of autonomy
Agents can be autonomous to different degrees:

- Some agents can be less autonomous with a fully deterministic sequence of steps
- In a more autonomous workflow, we let **LLM decides** if it needs to do a web search or use different tools

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/2.degrees_of_autonomy.png)

There is an spectrum:

![](https://github.com/DanialArab/images/blob/main/Agentic_AI/3.autonomy_spectrum.png)

Reference: https://www.deeplearning.ai/courses/agentic-ai/?utm_campaign=Short%20Course%20Announcements&utm_medium=email&_hsenc=p2ANqtz-96j0nIG5ukADk--vE0_v8FrNwu6KCV7SaUd1_Cyb0F6J5dPRBMX5B5bz7Bbulmld3CUaJ4DRpQB3cNV_rhKFdVNUJrWw&_hsmi=384075443&utm_content=384075443&utm_source=hs_email
