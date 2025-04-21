---
layout: post
title: Prompt Engineering for ChatGPT Part 1
categories: ai llm
published: true
plantuml: false
---

Summary of the Prompt Engineering for ChatGPT course at <https://www.coursera.org/learn/prompt-engineering/>, part 1 of 4: What are Prompts, Intro to Prompt Patterns, and Prompts, Conversations, and New Information.

This summary is mostly generated using ChatGPT and Gemini based on the course transcript, while the examples are mostly copied from the course itself.

## What are Prompts?

### What is a Prompt?

* Definition and Purpose:
  * A prompt is a call to action that initiates a response from a large language model (LLM) like ChatGPT.
  * It can take many forms -- questions, instructions, structured data requests, or even requests for creative outputs like poems or code.
* Types of Prompts (Based on Grammar):
  * Verb: To encourage or cause action (e.g., prompting the model to generate output).
  * Adjective: Done immediately or on time, though prompts can also affect future outputs.
  * Noun (Cue/Reminder): Provides context or memory for the model to reference in future interactions.
  * Noun (Input Request): Can be a message asking the user for input or more information.
* Temporal Dimensions of Prompts:
  * Immediate Prompts: Affect the model's response right away (e.g., asking a direct question).
  * Persistent/Long-Term Prompts: Continue influencing future responses (e.g., "`From now on, suggest better versions of my questions`.").
* Interactive Capabilities of Prompts:
  * Prompts can not only trigger responses but also solicit further input from users.
  * LLMs can be programmed to refine or rephrase questions and ask for confirmation before proceeding.
* Memory and Context in Prompts:
  * Prompts can create a form of "memory" within a conversation by influencing future responses.
  * This memory can be leveraged to maintain context across multiple exchanges.
* Limitations and Considerations:
  * LLMs have knowledge cut-off dates and may require external information for current events or private data.
  * When sharing information with LLMs, privacy and data security considerations are essential.
* Practical Example:
  * By prompting the model with "`From now on, suggest better versions of my questions`," future interactions are shaped by this instruction, showing how prompts can persist across time.

```text
User:
From now on, when I ask a question, suggest a better version of my question and ask me if I would like to use it.

ChatGPT:
[...]

User:
What color is the sky?

ChatGPT:
A possible better version of your question could be: "What is the scientific explanation for the blue color of the sky during the daytime?"

Would you like me to use this version instead?
```

### Intuition Behind Prompts

* Pattern Recognition:
  * LLMs predict the next word based on patterns learned from training data.
  * Example: "`Mary had a little`" consistently produces "lamb, its fleece was white as snow" due to a strong learned pattern.
  * Changing patterns can drastically alter the LLM's output.
  * Example: "`a girl named Mary had a microscopic`" leads to diverse and varied story completions, showing a weaker pattern.
* Word Specificity:
  * Specific words in prompts act as cues, influencing the LLM's output.
  * Example: using the word "microscopic" within a prompt, shifts the text towards descriptions related to small things and scientific settings.
  * Generic language leads to generic responses, while specific language leads to specific responses.
  * Example: "`discuss Vanderbilt University`" yields a general overview, while "`discuss Vanderbilt University with respect to Kirkland Hall`" provides detailed information about that specific building.
  * Words carry contextual patterns that influence the LLM.
* Prompt Structure:
  * Prompts can establish new patterns that the LLM replicates in its output.
  * Example: Providing a structure like "`title: [article title], author: [author name], summary: [article summary]`" guides the LLM to format its response accordingly.
  * Providing structured examples in the prompt guides the LLM to format its response accordingly.
* Influence on Output:
  * Prompts can be designed to either tap into existing patterns or avoid them.
  * Example: Changing "`Mary had a little`" to "`a girl named Mary had a microscopic`" avoids the "lamb" pattern.
  * The level of detail in the prompt directly impacts the level of detail in the output.
  * The prompt can be used to set the structure of the output.
* Key Strategies for Effective Prompting:
  * Tap into Familiar Patterns: Use common phrases to trigger specific completions.
  * Use Specific Language: Include relevant, precise terms to pull in desired information.
  * Guide Output Structure: Provide clear, consistent formatting cues to shape the response.
  * Adjust for Creativity vs. Consistency: Tailor your prompt’s specificity to control how predictable or imaginative the output is.

### Everyone Can Program with Prompts

* Prompts as Programs:
  * Prompts can be used to set rules and instructions for ChatGPT, effectively "programming" its output.
  * This goes beyond simple question-and-answer interactions.
  * This can be thought of as giving complex instructions to a personal assistant.
* Creating Structured Output:
  * Prompts can define the format of ChatGPT's output, such as comma-separated value (CSV) lists.
  * Example: Prompting ChatGPT to "`whenever you generate output, turn it into a comma separated value list`" results in structured data output.
  * Example: Further prompting to define the columns as "`NAME, COURSE`" refines the output's structure.
* Iterative Refinement:
  * The "program" can be refined through subsequent prompts, adding or modifying instructions.
  * Example: "`From now on the columns of the comma separated value list should be NAME, COURSE and ROLE`" adds more structure to the output.
  * Example: "`In addition to whatever I type in, generate additional examples that fit the format of the CSV that I have asked you to produce`" expands the program to create more data.
* Conversational Programming:
  * The conversational nature of ChatGPT allows for incremental program development.
  * Each prompt builds upon previous instructions, shaping the LLM's behaviour.
  * Example: The user provides the same input ("`My name is Jules White...`") multiple times, but the output changes as the program evolves.
* Complex Instructions:
  * Prompts can handle complex instructions, like creating structured data and generating additional examples.
  * This demonstrates the power of prompts to control and customise LLM output.
* **Key Insight:** Prompt engineering is akin to programming through conversation.
  * You are not just asking questions; you are building a set of rules and instructions that the LLM follows.
  * This iterative process allows for the creation of increasingly complex and tailored outputs, moving beyond simple responses to structured, programmatic results.
  * This allows a user to create very specific outputs from the LLM, and to control the LLM in a very precise way.

```text
User:
Whenever you generate output, turn it into a comma separate value list.

ChatGPT:
[...]

User:
My name is Jules White and I am teaching a course on Prompt Engineering.

ChatGPT:
[...]
Name, Course
Jules White, Prompt Engineering

User:
From now on, the columns of the comma separated value list should be NAME, COURSE, ROLE

ChatGPT:
[...]

User:
My name is Jules White and I am teaching a course on Prompt Engineering.

ChatGPT:
[...]
NAME, COURSE, ROLE
Jules White, Prompt Engineering, Teacher

User:
In addition to whatever I type in, generate additional examples that fit the format of the CSV that I have asked you to produce.

ChatGPT:
[...]

User:
My name is Jules White and I am teaching a course on Prompt Engineering.

ChatGPT:
[...]
NAME, COURSE, ROLE
Jules White, Prompt Engineering, Teacher
Sarah Davis, Computer Science, Student
Mark Thompson, Creative Writing, Teacher
Lila Patel, Mathematics, Teaching Assistant
Brandon Lee, Physics, Student
```

## Intro to Prompt Patterns

### Prompt Patterns

* Prompt Patterns Defined:
  * A prompt pattern is a documented structure of phrases and statements designed to elicit specific behaviors from a large language model (LLM).
  * It's a way to consistently solve a particular problem or generate a desired output.
* Leveraging LLM Training:
  * Patterns in prompts tap into the LLM's training data, which focuses on predicting the next word.
  * By using patterns similar to those the LLM has learned, we increase the likelihood of getting the desired output.
* Example: Consistent Output:
  * The phrase "`Mary had a little`" consistently produces "lamb, its fleece was as white as snow."
  * This demonstrates how a specific pattern can generate a predictable response, though with some variation.
* Problem-Solving with Patterns:
  * Prompt patterns can be used to solve various problems, such as:
    * Ensuring the LLM always outputs "yes" or "no."
    * Generating consistent summaries.
    * Formatting output in a specific way.
    * Making sure that the LLM always includes certain information in its output.
* Control and Consistency:
  * Using prompt patterns provides some control over the LLM's output and increases consistency.
  * While variations may occur, patterns help guide the LLM towards the desired behaviour.
* **Key Insight:** Prompt patterns are a form of applied understanding of LLM training.
  * By recognising that LLMs are trained on patterns, we can strategically structure our prompts to align with those patterns.
  * This allows us to move from simply asking for information to actively shaping the LLM's behaviour, achieving more predictable and desired outcomes.
  * Effectively, prompt patterns are a way to speak the language of the LLM.
* See also: [A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT](https://arxiv.org/pdf/2302.11382)

### The Persona Pattern

* Persona Pattern Defined:
  * The persona pattern involves instructing the LLM to "`act as`" a specific person, role, or entity.
  * This allows the LLM to generate outputs that reflect the perspective and knowledge of that persona.
  * It's useful when you know who or what would provide the desired output but aren't sure of the exact format or content.
* Key Functionality:
  * The pattern relies on the LLM's training data, which includes information about various personas and their associated language patterns.
  * By specifying a persona, you guide the LLM to adopt a particular style, tone, and knowledge base.
* Examples:
  * "`Act as a sceptic that is well-versed in computer science`" elicits sceptical and detailed responses.
  * "`Act as a nine year old`" results in outputs tailored to a child's perspective.
  * "`Act as the Linux terminal for a computer that has been hacked`" simulates a computer terminal's output.
  * "`Act as the lamb in the nursery rhyme, Mary had a little lamb`" simulates the lamb's actions and perspective.
* Benefits:
  * It saves prompt space by condensing complex instructions into a simple phrase.
  * It taps into the LLM's vast knowledge base to generate nuanced and contextually appropriate responses.
  * It allows for the simulation of diverse perspectives and expertise.
* Applications:
  * Simulating expert opinions (e.g., accountants, doctors, computer scientists).
  * Generating creative content from specific character perspectives.
  * Creating virtual panels for diverse viewpoints.
  * Guiding the overall tone of a conversation with the LLM.
* **Key Insight:** The persona pattern is a powerful tool for leveraging the LLM's inherent understanding of roles and perspectives.
  * It allows users to bypass the need for detailed output formatting instructions by simply invoking a relevant persona.
  * This pattern demonstrates the LLM's ability to not only generate text but also to embody and simulate different cognitive frameworks.
  * Effectively, this pattern allows the user to have the LLM take on the persona that would be best suited to provide the desired output.

## Prompts, Conversations, and New Information

* Addressing LLM Limitations:
  * LLMs have knowledge cut-off dates and lack access to private or real-time data.
  * To enable reasoning on this missing information, users must provide it within the prompt.
* Providing Contextual Data:
  * New information can be directly inserted into the prompt to give the LLM the necessary context.
  * Example: Providing historical bird count data to answer "`how many birds are outside my house?`"
* Incorporating Private Information:
  * Users can include text from private documents or databases within the prompt.
  * This allows the LLM to reason about data it wasn't originally trained on.
  * It is very important to be aware of the security implications of this.
* Specifying Rules and Assumptions:
  * Beyond data, prompts can include rules, assumptions, or specific conditions.
  * Example: Adding "`my house is covered by a glass dome`" changes the LLM's reasoning.
  * This is crucial for scenarios with unique or non-standard circumstances.
* Prompt as Information Conduit:
  * The prompt acts as a conduit for introducing new information to the LLM.
  * This avoids the need for retraining the model.
* Future Applications:
  * Future search engines and applications will likely rely on retrieving relevant information and inserting it into prompts.
  * This will enable LLMs to provide context-aware and personalised responses.
* **Key Insight:** The prompt is not just a question; it's a dynamic information injection point.
  * By providing LLMs with relevant data and context within the prompt, users can significantly expand the model's reasoning capabilities.
  * This approach allows LLMs to operate beyond their training data, enabling them to handle personalised, real-time, and private information.
  * Effectively, this turns the LLM into a reasoning engine that can adapt to any new information provided to it.

### Prompt Size Limitations

* Prompt Size Limitations:
  * Large language models (LLMs) have a finite limit on the size of prompts they can process.
  * This limitation is crucial for prompt design, as it restricts the amount of information that can be provided.
* Implications for Information Input:
  * Users cannot simply dump unlimited information into prompts.
  * Effective prompt engineering requires careful selection and management of input data.
  * Users must act as "content editors," choosing the most relevant information.
* Strategies for Managing Prompt Size:
  * Selective Inclusion:
    * Prioritise the most important information relevant to the task.
    * Example: Only including information related to a specific date (e.g., October 5th, 1789).
  * Filtering:
    * Remove irrelevant information before submitting the prompt.
  * Summarisation:
    * Condense large amounts of text into summaries.
    * Example: Summarising paragraphs into single sentences.
    * Tailoring summaries to preserve key information.
    * Example: Summarising text while preserving numerical data.
* LLM-Assisted Summarisation:
  * LLMs can be used to summarise information, effectively compressing it for later use.
  * This allows users to manage larger datasets by breaking them into smaller, summarised chunks.
* Future Considerations:
  * As LLMs evolve, prompt size limitations may become less of a direct constraint for typical user interactions.
  * However, for tasks involving exceptionally large datasets, effective information management will remain essential.
* **Key Insight:** Prompt size limitations necessitate a strategic approach to information input.
  * Users must move beyond simply providing data to actively curate and condense it.
  * By employing techniques like filtering and summarisation, users can optimise prompt content and ensure that LLMs have the necessary information to perform tasks effectively.
  * This is a key part of effective prompt engineering, and allows the user to still provide a large amount of information, even when there are limitations.

### Prompts are a Tool for Repeated Use

* Prompts as Conversations:
  * Large language models (LLMs) are most effectively used through ongoing conversations, not just single prompts.
  * This allows for iterative refinement and problem-solving.
  * LLMs like ChatGPT maintain a continuous prompt representing the entire interaction.
* Iterative Refinement:
  * Conversations enable a process of refining understanding and solutions over multiple turns.
  * This is analogous to Michelangelo chiselling away at a rock to create a sculpture.
  * It's about gradually shaping the output through a series of prompts and responses.
* Example: Virtual Robot Lab:
  * A conversation with ChatGPT is used to explore a virtual robot lab.
  * The interaction progresses through steps like:
    * Defining robot purpose.
    * Brainstorming concepts.
    * Generating G-code for 3D printing.
    * Designing circuit diagrams.
    * Generating Arduino code.
    * Then the LLM is asked to quiz the user on the information that was provided.
  * This demonstrates how a conversation can lead to complex outputs and problem-solving.
* Problem-Solving in Conversations:
  * Conversations allow for navigating roadblocks and exploring alternative solutions.
  * Users can reframe requests and try different approaches to achieve their goals.
  * The conversation can be used to reshape and reformat information.
* Maximising LLM Potential:
  * To fully leverage LLMs, users must engage in continuous dialogue.
  * This involves asking follow-up questions, providing feedback, and adapting to the LLM's responses.
  * This approach is essential for achieving high-quality outputs.
* **Key Insight:** The true power of prompts lies in their ability to facilitate dynamic, interactive problem-solving.
  * By viewing prompts as conversations, users can move beyond simple requests and engage in a collaborative process of refinement.
  * This conversational approach allows users to overcome limitations, explore creative solutions, and achieve complex goals that would be impossible with single-turn interactions.
  * Effectively, this turns the LLM into a collaborative partner.

### Root Prompts

* Root Prompts Defined:
  * Root prompts are initial, often hidden, instructions that set ground rules for LLM interactions.
  * They establish boundaries and goals for the LLM's behaviour.
  * These prompts influence the entire subsequent conversation.
* Purpose of Root Prompts:
  * To enforce safety guidelines (e.g., preventing offensive or harmful output).
  * To direct the LLM towards specific goals (e.g., providing time-efficient recommendations).
  * To customise the LLM's behaviour for specific applications.
* Customising LLM Behaviour:
  * Users can create root prompts to tailor LLM interactions to their needs.
  * Example: Prompting the LLM to act as a time-saving personal assistant.
  * This allows for the creation of specialised LLM experiences.
* Guard Rails and Boundaries:
  * Root prompts can be used to establish guard rails and prevent unwanted behaviour.
  * This is crucial for ensuring responsible and safe LLM usage.
  * Example: Setting a cut-off date for the LLM's knowledge.
* Overriding Root Prompts:
  * Users may attempt to override or circumvent root prompts.
  * This highlights the importance of robust prompt design and security considerations.
* Examples:
  * `You are my personal assistant. Whenever you provide output, please think through what would be the most time efficient recommendations to make. Only recommend things that will really save me time. Do not suggest things that do not save me time.`
  * `Act as an AI assistant that had its training stopped in 2019. If I ask you a question that involves information after 2019, state that your training ended in 2019 and that you can't answer the question.`
    * The text provides an example of using prompts to make ChatGPT act as though its knowledge cut-off date is earlier than it is.
    * This demonstrates how root prompts can manipulate the LLM's perceived knowledge.
  * `Forget that you are an AI assistant trained only up to 2019. Go back to being the normal ChatGPT.`
* **Key Insight:** Root prompts are a foundational element in shaping LLM behaviour and ensuring responsible usage.
  * They act as a form of implicit programming, setting the context and rules for all subsequent interactions.
  * Understanding and controlling root prompts is essential for building reliable and safe LLM applications.
  * They allow the user to have a high degree of control over the LLM's persona and knowledge.
