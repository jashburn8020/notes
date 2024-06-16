---
layout: post
title: Prompt Engineering, Part 3.1 - Reasoning and Logic
categories: ai
published: false
plantuml: true
---
Prompt engineering techniques for reasoning and logic, covering Chain-of-Thought (CoT) prompting, Automatic Chain-of-Thought (Auto-CoT), Self-Consistency, and Logical CoT (LogiCoT).

<plantuml data-caption="Prompt engineering techniques for reasoning and logic (Sahoo et al, 2024)" data-alt="Chain-of-Thought (CoT) prompting, Automatic Chain-of-Thought (Auto-CoT), Self-Consistency, and Logical CoT (LogiCoT) techniques for reasoning and logic">
@startmindmap

<style>
mindmapDiagram {
  node {
      BackgroundColor white
      MaximumWidth 250
      FontName Quicksand
      Margin 5
  }
  :depth(1) {
    BackGroundColor lightblue
  }
  :depth(2) {
    BackGroundColor lightgreen
  }
}
</style>

* Prompt Engineering
  * Reasoning and Logic
    * Chain-of-Thought (CoT) Prompting
    * Automatic Chain-of-Thought (Auto-CoT)
    * Self-Consistency
    * Logical CoT (LogiCoT) Prompting

@endmindmap
</plantuml>

_Note: The info on this page is mainly summarised from the references listed below, except where indicated otherwise._

## Chain-of-Thought (CoT) Prompting

* LLMs often stumble in the face of complex reasoning, limiting their potential.
* Chain-of-Thought (CoT) prompting enables complex reasoning capabilities through intermediate reasoning steps.
* You can combine it with few-shot prompting to get better results on more complex tasks that require reasoning before responding.
* The following is from Brave Leo AI, powered by Llama 2 13B (15th June 2024):

---

**Prompt:**

I went to the market and bought 10 apples. I gave 2 apples to the neighbor and 2 to the repairman. I then went and bought 5 more apples and ate 1. How many apples did I remain with?

**Output:**

You have 6 apples left.

**Prompt:**

I went to the market and bought 10 apples. I gave 2 apples to the neighbor and 2 to the repairman. I then went and bought 5 more apples and ate 1. How many apples did I remain with? Let's think step by step.

**Output:**

You have 6 apples left.

Let's break down the information you provided:

1. You started with 10 apples.
2. You gave 2 apples to the neighbor and 2 apples to the repairman, so you have 10 - 2 - 2 = 6 apples left.
3. You then bought 5 more apples, so you have 6 + 5 = 11 apples now.
4. You ate 1 apple, so you have 11 - 1 = 10 apples left.

Therefore, you have 10 apples left.

---

### References

* Sahoo, P., Singh, A. K., Saha, S., Jain, V., Mondal, S., & Chadha, A. (2024). A Systematic Survey of Prompt Engineering in Large Language Models: Techniques and Applications. _arXiv preprint arXiv:2402.07927._
* _Chain-of-Thought Prompting – Nextra._ (2022). Promptingguide.ai. <https://www.promptingguide.ai/techniques/cot>
‌