---
layout: post
title: Prompt Engineering, Part 1 - Introduction
categories: ai
plantuml: true
---
A brief introduction to prompt engineering and a taxonomy of techniques.

This series of articles briefly describes the various techniques used in prompt engineering.

_Note: The info on this page is mainly summarised from the references listed below, except where indicated otherwise._

## Introduction

* Technique for enhancing the capabilities of pre-trained large language models (LLMs) and vision-language models (VLMs).
* A mechanism to fine-tune model outputs through carefully crafted instructions, enables these models to excel across diverse tasks and domains.
* Involves strategically designing task-specific instructions (prompts), to guide model output without altering parameters.
  * **Prompt**: Natural language text describing the task that an AI should perform.
* Different from traditional paradigms, where model retraining or extensive fine-tuning is often required for task-specific performance.
* A prompt for a text-to-text language model can be:
  * a **query**, e.g., "what is Fermat's little theorem?",
  * a **command**, e.g., "write a poem about leaves falling", including assigning a **role** such as "act as a native French speaker", or
  * a longer statement including **context**, **instructions**, and **conversation history**.
* A prompt may include a few **examples** for which a model to learn.
* With a text-to-image or a text-to-audio model, a typical prompt is a description of a desired output, e.g.,
  * "a high-quality photo of an astronaut riding a horse"
  * "lo-fi slow BPM electro chill with organic samples".
* Prompting a text-to-image model
  * may involve adding, removing, emphasizing and re-ordering words
  * to achieve a desired subject, style, layout, lighting, and aesthetic.

## Taxonomy of Techniques

<plantuml data-caption="Taxonomy of prompt engineering techniques in LLMs, organised around application domains" data-alt="Taxonomy of prompt engineering techniques in LLMs">
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
  * New Tasks Without Extensive Training
    * Zero-Shot Prompting
    * Few-Shot Prompting
  * Reasoning and Logic
    * Chain-of-Thought (CoT) Prompting
    * Automatic Chain-of-Thought (Auto-CoT)
    * Self-Consistency
    * Logical CoT (LogiCoT) Prompting
    * Chain-of-Symbol (CoS) Prompting
    * Tree-of-Thoughts (ToT) Prompting
    * Graph-of-Thought (GoT) Prompting
    * System 2 Attention Prompting
    * Thread of Thought (ThoT) Prompting
    * Chain of Table Prompting
  * Reduce Hallucination
    * Retrieval Augmented Generation (RAG)
    * ReAct Prompting
    * Chain-of-Verification (CoVe)
    * Chain-of-Note (CoN) Prompting
    * Chain-of-Knowledge (CoK) Prompting
  * User Interaction
    * Active-Prompt
  * Fine-Tuning and Optimization
    * Automatic Prompt Engineer (APE)
  * Knowledge-Based Reasoning and Generation
    * Automatic Reasoning and Tool-use (ART)
  * Improving Consistency and Coherence
    * Contrastive Chain-of-Thought Prompting (CCoT)
  * Managing Emotions and Tone
    * Emotion Prompting
  * Code Generation and Execution
    * Scratchpad Prompting
    * Program of Thoughts (PoT) Prompting
    * Structured Chain-of-Thought (SCoT) Prompting
    * Chain of Code (CoC) Prompting
  * Optimization and Efficiency
    * Optimization by Prompting
  * Understanding User Intent
    * Rephrase and Respond (RaR) Prompting
  * Metacognition and Self-Reflection
    * Take a Step Back Prompting

@endmindmap
</plantuml>

## References

* Sahoo, P., Singh, A. K., Saha, S., Jain, V., Mondal, S., & Chadha, A. (2024). A Systematic Survey of Prompt Engineering in Large Language Models: Techniques and Applications. _arXiv preprint arXiv:2402.07927._
* Wikipedia Contributors. (2024, June 5). _Prompt engineering._ Wikipedia; Wikimedia Foundation. <https://en.wikipedia.org/wiki/Prompt_engineering>
