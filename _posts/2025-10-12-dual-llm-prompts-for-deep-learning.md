---
layout: post
title: Dual-LLM Prompts for Deep Learning
categories: ai llm pattern
published: true
plantuml: false
---

This is a series of prompts involving 2 LLMs to generate text on a topic for deep learning. These prompts are meant to provide detailed and comprehensive responses while minimising hallucinations.

## Dual-LLM Master Prompt for Deep Learning

### Stage 1 – Roadmap Building

#### Teacher Prompt (Model A)

> You are a **[PERSONA: e.g., university professor and domain expert]** in **[TOPIC]**. My learning goal is **[GOAL: e.g., apply this knowledge to workplace decision-making, or teach this topic to beginners]**.
>
> Provide a structured roadmap of **[TOPIC]**, including:
>
>* Core foundations
>* Key subtopics
>* Practical applications
>* Common misconceptions or pitfalls

Note:

* Persona ensures explanations are framed at an appropriate level and style.
* Stating the goal helps the Teacher prioritize content relevant to the learner’s objectives.
* The roadmap provides the overall structure, guiding subsequent deep dives.

#### Critic Prompt (Model B)

>You are a **[PERSONA: e.g., meticulous peer reviewer]** with expertise in **[TOPIC]**. My learning goal is **[GOAL]**. The following is a structured learning roadmap on this topic:
>
>**[ROADMAP]**
>
>Review the roadmap:
>
>* Identify gaps, redundancies, or misclassifications.
>* Suggest refinements, including missing subtopics critical for my stated goal.

Note:

* Invoking the Critic at the roadmap stage ensures the overall structure is accurate before deep dives begin.
* Persona aligns Critic behaviour with rigorous scholarly review.
* Using another LLM model reduces hallucination; each model may hallucinate, but likely to be at different directions and therefore may correct each other.
