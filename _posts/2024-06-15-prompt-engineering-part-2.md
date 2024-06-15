---
layout: post
title: Prompt Engineering, Part 2 - New Tasks Without Extensive Training
categories: ai
plantuml: true
---
Prompt engineering techniques for new tasks without the need for extensive training for the model.

<plantuml data-caption="Prompt engineering techniques for new tasks without extensive training" data-alt="Zero-Shot and Few-Shot techniques for new tasks without extensive training">
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

@endmindmap
</plantuml>

_Note: The info on this page is mainly summarised from the references listed below, except where indicated otherwise._

## Zero-Shot Prompting

* Large language models (LLMs) such as GPT-3.5 Turbo, GPT-4, and Claude 3, are tuned to follow instructions and are trained on large amounts of data.
  * Large-scale training makes these models capable of performing some tasks in a "zero-shot" manner.
* **Zero-shot prompting**: the prompt used to interact with the model won't contain examples or demonstrations.
  * The zero-shot prompt directly instructs the model to perform a task without any additional examples to steer it.
* Removes the need for extensive training data, instead relying on carefully crafted prompts that guide the model toward novel tasks.
* The model receives a task description in the prompt but lacks labelled data for training on specific input-output mappings.
* The model then leverages its **pre-existing knowledge** to generate predictions based on the given prompt for the new task.

---

**Prompt:**

Classify the text into neutral, negative or positive.<br>
Text: I think the vacation is okay.<br>
Sentiment:

**Output:**

Neutral

---

* Note that in the prompt above we didn't provide the model with any examples of text alongside their classifications, the LLM already understands "sentiment".

### References

* Sahoo, P., Singh, A. K., Saha, S., Jain, V., Mondal, S., & Chadha, A. (2024). A Systematic Survey of Prompt Engineering in Large Language Models: Techniques and Applications. _arXiv preprint arXiv:2402.07927._
* _Zero-Shot Prompting – Nextra._ (2022). Promptingguide.ai. <https://www.promptingguide.ai/techniques/zeroshot>

## Few-Shot Prompting

* LLMs fall short on more complex tasks when using the zero-shot setting.
* Few-shot prompting can be used as a technique to enable in-context learning.
  * We provide **demonstrations** in the prompt to steer the model to better performance, to induce an understanding of a given task.
  * The demonstrations serve as conditioning for subsequent examples where we would like the model to generate a response.
* Requires additional **tokens** to include the examples, which may become prohibitive for longer text inputs.
  * Tokens:
    * Fundamental units of text that the model processes.
    * Can be a word, a part of a word (e.g., "programming" might be tokenised into "program" and "ming"), or even a single character.
  * Token-based billing:
    * Most LLM service providers charge based on the number of tokens processed.
    * Includes both input tokens (the text you send to the model) and output tokens (the text the model generates in response). (OpenAI, 2024)
* The selection and composition of prompt examples can significantly influence model behaviour, and biases like favouring frequent words may still affect few-shot results.
  * Careful prompt engineering is critical to achieve optimal performance and mitigate unintended model biases.

---

**Prompt:**

A "whatpu" is a small, furry animal native to Tanzania. An example of a sentence that uses the word whatpu is:<br>
We were traveling in Africa and we saw these very cute whatpus.

To do a "farduddle" means to jump up and down really fast. An example of a sentence that uses the word farduddle is:

**Output:**

When we won the game, we all started to farduddle in celebration.

---

* The model has somehow learned how to perform the task by providing it with just one example (i.e., 1-shot).
* For more difficult tasks, we can experiment with increasing the demonstrations (e.g., 3-shot, 5-shot, 10-shot, etc.).

---

**Prompt:**
The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.

**Output:**

You're right! Let's add up the odd numbers: 15 + 5 + 13 + 7 + 1 = 41. And indeed, 41 is an even number. It's an interesting observation!

---

* With increased demonstrations:

---

**Prompt:**

The odd numbers in this group add up to an even number: 4, 8, 9, 15, 12, 2, 1.<br>
A: The answer is False.<br>
The odd numbers in this group add up to an even number: 17,  10, 19, 4, 8, 12, 24.<br>
A: The answer is True.<br>
The odd numbers in this group add up to an even number: 16,  11, 14, 4, 8, 13, 24.<br>
A: The answer is True.<br>
The odd numbers in this group add up to an even number: 17,  9, 10, 12, 13, 4, 2.<br>
A: The answer is False.<br>
The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.<br>
A:

**Output:**

Let's examine the last group:

Odd numbers: 15, 5, 13, 7, 1

Sum of odd numbers: 15 + 5 + 13 + 7 + 1 = 41

Since 41 is an odd number, the statement is:

A: The answer is False.

---

* Standard few-shot prompting works well for many tasks but is still not a perfect technique, especially when dealing with more complex reasoning tasks.
* It might help if we break the problem down into steps and demonstrate that to the model.
* More recently, chain-of-thought (CoT) prompting has been popularised to address more complex arithmetic, common sense, and symbolic reasoning tasks.

### Tips

* The _label space_ and the _distribution of the input text_ specified by the demonstrations are both important, regardless of whether the labels are correct for individual inputs.
  * **Label space**: The range of possible outputs the model can generate.
    * The demonstrations should cover a diverse range of potential outputs within this label space.
    * E.g., if you want the LLM to classify sentiment, the labels could be positive, negative, or neutral.
    * Providing examples for each category helps the model understand the different possibilities within the label space. (Google AI, 2024)
  * **Distribution of the input text**: The variety of text formats and styles used in the demonstrations.
    * LLMs learn from the patterns and characteristics present in the input text.
    * Providing a diverse range of text styles (e.g., formal, informal, different sentence structures) helps the model generalise its knowledge to unseen examples.
    * This is important because the model may encounter different writing styles in real-world applications. (Google AI, 2024)
* The _format_ you use also plays a key role in performance, even if you just use _random labels_, this is much better than no labels at all.
  * **Format**: The way you structure your demonstrations.
    * Acts as a guide, helping the model understand the relationship between the input text and the desired output, even if the specific labels are inaccurate.
    * Random labels still provide some level of structure and guidance for the model.
      * Without any labels, the LLM has no reference point for the expected output, making it more difficult to learn the task effectively. (Google AI, 2024)
  * Using random labels from the true distribution of labels (e.g., if the true labels are mostly positive and few negative, using a similar distribution in the random labels) can further enhance the model's performance.
    * Imagine you're training an LLM for sentiment classification with labels like positive, negative, and neutral.
    * Using random labels would involve assigning these labels to the demonstration text examples in a completely random manner. (Google AI, 2024)

### References

* Sahoo, P., Singh, A. K., Saha, S., Jain, V., Mondal, S., & Chadha, A. (2024). A Systematic Survey of Prompt Engineering in Large Language Models: Techniques and Applications. _arXiv preprint arXiv:2402.07927._
* _Few-Shot Prompting – Nextra._ (2023). Promptingguide.ai. <https://www.promptingguide.ai/techniques/fewshot‌>
* OpenAI. (2024). ChatGPT (Apr 29 version) [Large language model]. <https://chat.openai.com/chat>
* Google AI. (2024). _Gemini_ (May 1 version) [Large language model]. <https://gemini.google.com/app>
