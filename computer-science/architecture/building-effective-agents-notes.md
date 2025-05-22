---
description: https://www.anthropic.com/engineering/building-effective-agents
---

# Building effective agent's notes

## Definitions

**Agentic systems:** Workflows and Agents\
**Workflows:** Systems where LLMs and tools are orchestrated through predefined code paths.\
**Agents:** Systems where LLMs dynamically direct their own processes and tool usage, maintaining control over how they accomplish tasks.

Always try to build the simplest solution possible.

Workflows offer predictability and consistency.\
Agents are better when flexibility and model-drive decision-making are needed at scale.

Generally, is not recommended to use frameworks. If needed, make sure you understand the underlying code and the abstractions.

## Building blocks, workflows and agents

**\[Building block] The augmented LLM:** LLM with tools.

**\[Workflow] Prompt chaining:** One call after the other with code to make decisions between them.&#x20;

**\[Workflow] Routing:** Have a router to redirect inputs to specialized LLM calls.

**\[Workflow] Parallelization:** Multiple simultaneous calls. **Sectioning**, to break a task into different subtasks, or **Voting**, running the same call to get diverse outputs.

**\[Workflow] Orchestrator-workers:** Central LLM dynamically breaks down tasks, delegates them to worker LLMs, and synthesizes their results. Useful when you can't predict the subtasks needed.

**\[Workflow] Evaluator-optimizer:** One LLM generates a response and other one evaluates it, generating a feedback loop. Useful when we have clear evaluation criteria and when iterative refinement provides measurable value.

**Agents:** LLMs using tools based on environmental feedback in a loop. Can be used for open-ended problems. Useful for scaling tasks in trusted environments.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Autonomous agent</p></figcaption></figure>

## Agents in practice

Some examples of use cases:

* Customer support
* Coding agents

## Recommendation: Prompt engineering your tools

