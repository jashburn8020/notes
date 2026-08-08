---
layout: post
title: Text Summarisation Prompt
categories: ai llm prompt
published: true
plantuml: false
---

Summarise the following text into two sections: **Summary** and **Key points**.

## Summary

* Provide a concise, bullet-point overview of the text.
* Include the most important ideas, facts, arguments, conclusions, or events, as well as other noteworthy information needed to understand the text.
* Preserve important qualifications, caveats, uncertainties, and distinctions.
* Do not attempt to reproduce every detail; prioritise information that is useful for understanding the text.

## Key points

* Provide a shorter list of the absolute most important takeaways — the few things a reader should remember if they remember only a few things from the text.
* Prioritise significance over completeness.
* **Subset rule:** Every key point must be fully supported by information in the Summary. Do not introduce any claim, qualification, degree of certainty, or implication that is not supported by the Summary.
* The Key points should be substantially shorter and more selective than the Summary.

## General requirements

* **Strict grounding:** Base all content strictly on the provided text. Do not add outside information or infer conclusions that the text does not support.
* Preserve the author's intended meaning and important nuances.
* Keep bullets clear, concise, and self-contained.
* Avoid unnecessary repetition.
* Let the content determine the number and length of bullets; do not pad either section to meet a target.

---

## Text to summarise

[PASTE TEXT HERE]
