---
layout: post
title: Prompt Engineering for ChatGPT Part 4
categories: ai llm
published: true
plantuml: false
---

Summary of the [Prompt Engineering for ChatGPT course at Coursera](https://www.coursera.org/learn/prompt-engineering/), part 4 of 4, covering Ask for Input Pattern, Outline Expansion Pattern, Menu Actions Pattern, Fact Check List Pattern, Tail Generation Pattern, and Semantic Filter Pattern.

* **Ask for Input Pattern**
  * To instruct the LLM to listen to the rules or instructions provided in the prompt and then explicitly ask the user for the input to which those rules should be applied.
  * `Whenever I ask you to write a prompt for me to accomplish a task, list what the task is, list alternative approaches for completing the task, and then write a prompt for yourself for each approach. When you are done, ask me of the next prompt to create alternatives for. Ask me for the first task.`
* **Outline Expansion Pattern**
  * To overcome the input and output limitations of LLMs by enabling the generation of large pieces of work in smaller, manageable sections by creating an outline and iteratively expanding specific points within that outline.
  * `Act as an outline expander. Generate a bullet point outline based on the input that I give you and then ask me for which bullet point you should expand on. Create a new outline for the bullet point that I select. At the end, ask me for what bullet point to expand next. Ask me for what to outline.`
* **Menu Actions Pattern**
  * To create a "menu" of operations (pre-defined prompts) that can be reused within a conversation with an LLM via specific keywords or phrases.
  * `Whenever I type: "add FOOD", you will add FOOD to my grocery list and update my estimated grocery bill. Whenever I type "remove FOOD", you will remove FOOD from my grocery list and update my estimated grocery bill. Whenever I type "save" you will list alternatives to my added FOOD to save money. At the end, you will ask me for the next action. Ask me for the first action.`
* **Fact Check List Pattern**
  * To generate a list of the underlying facts presented in the LLM's output that can help users identify key pieces of information that need to be verified for accuracy.
  * `Whenever you output text, generate a set of facts that are contained in the output. The set of facts should be inserted at the end of the output. The set of facts should be the fundamental facts that could undermine the veracity of the output if any of them are incorrect.`
* **Tail Generation Pattern**
  * To generate a "tail" at the end of an LLM's output as a way to prevent the LLM from forgetting its initial instructions over a long conversation.
  * `Whenever I ask you to write a prompt for me to accomplish a task, list what the task is, list alternative approaches for completing the task, and then write a prompt for yourself for each approach. When you are done, ask me for the next prompt to create alternatives for. Ask me what I want you to write a prompt for.`
* **Semantic Filter Pattern**
  * To instruct the LLM to act as a filter, removing or keeping information based on semantic understanding rather than just keyword matching.
  * `Filter this information to remove all dates and rewrite the text as little as possible to fix the issues caused by the date removals.`
  * `Filter the information below to remove any information that would help someone figure out that the patient has diabetes. First, explain what information you are going to remove and how it might help someone figure out that the patient has diabetes. Then, provide the filtered information.`

_The following summary is mostly generated using ChatGPT and Gemini based on the course transcript, while the examples are mostly copied from the course itself._

---

* [Prompt Patterns III](#prompt-patterns-iii)
  * [Ask for Input Pattern](#ask-for-input-pattern)
  * [Combining Patterns](#combining-patterns)
  * [Outline Expansion Pattern](#outline-expansion-pattern)
  * [Menu Actions Pattern](#menu-actions-pattern)
  * [Fact Check List Pattern](#fact-check-list-pattern)
  * [Tail Generation Pattern](#tail-generation-pattern)
  * [Semantic Filter Pattern](#semantic-filter-pattern)

## Prompt Patterns III

### Ask for Input Pattern

* Ask for Input Pattern:
  * This pattern is used to instruct the LLM to listen to the rules or instructions provided in the prompt and then explicitly ask the user for the input to which those rules should be applied.
  * It prevents the LLM from immediately generating a response or taking action before receiving the specific input from the user.
  * This is useful for creating interactive experiences and controlling the flow of the conversation.
* Rationale:
  * Without this pattern, LLMs might prematurely generate responses or examples based on the rules provided, rather than waiting for the user's specific input.
  * It allows for a more controlled and user-driven interaction.
  * It's particularly helpful in scenarios where the user needs to provide context or data after setting the stage with rules or instructions.
* Implementation:
  * After describing the rules, instructions, or desired behaviour in the prompt, the very last sentence should explicitly ask the LLM to request the user's input.
  * Examples include: "Ask me for the first task," "What is the first idea you'd like to explore?", "Ask me for the topic."
  * This signals to the LLM that it should pause and wait for the user to provide the necessary information to proceed.
* Benefits:
  * Creates a more predictable and controlled interaction with the LLM.
  * Prevents the LLM from generating irrelevant or premature responses.
  * Allows the user to provide specific context or data after the rules are established.
  * Facilitates the creation of interactive applications or conversational flows.
* Key Considerations:
  * While very reliable, LLMs are stochastic, so it might not work 100% of the time. However, it is generally very effective.
  * The phrasing of the request for input should be clear and directly ask the user for what is needed next.
* **Key Insight:** By explicitly instructing the LLM to "ask for input" at the end of a prompt that sets rules or expectations, users can effectively pause the LLM's immediate response and maintain control over the interaction by providing the specific data or context required.
  * This pattern is crucial for building interactive and user-driven experiences with LLMs.
  * It ensures that the LLM waits for the user's specific needs before applying the defined rules.
  * It helps to avoid the LLM generating unwanted content or taking premature actions.

```text
--- WITHOUT PATTERN ---

> User
Whenever I ask you to write a prompt for me to accomplish a task, list what the task is, list alternative approaches for completing the task, and then write a prompt for yourself for each approach. When you are done, ask me of the next prompt to create alternatives for.

> ChatGPT
Certainly! Let's start by creating a prompt for the task of "organizing a cluttered desk." Here are three alternative approaches for completing the task:

1. [...]
2. [...]
3. [...]

Now I'll write a prompt for myself for each approach:

Prompt for Approach 1:
[...]

--- WITH PATTERN ---

> User
Whenever I ask you to write a prompt for me to accomplish a task, list what the task is, list alternative approaches for completing the task, and then write a prompt for yourself for each approach. When you are done, ask me of the next prompt to create alternatives for.

Ask me for the first task.

> ChatGPT
Certainly! Let's begin. What is the first task you would like me to create alternative approaches and prompts for?
```

### Combining Patterns

* Combining Prompting Patterns:
  * Building sophisticated prompts often involves combining multiple prompting patterns.
  * Instead of looking for a single pattern to solve a problem, consider which patterns can address different aspects of it.
  * This allows for more powerful and nuanced prompts.
* Examples of Combined Patterns:
  * The Ask for Input pattern can be combined with many other patterns, such as Alternative Approaches and Game Play.
  * In the Alternative Approaches example, Ask for Input was used to control the flow after setting the rules.
  * The Game Play pattern likely incorporates Ask for Input and the Persona pattern.
* Approach to Combining Patterns:
  * Identify the fundamental components of the problem you're trying to solve.
  * Determine if there are existing patterns that can address each of these components.
  * Aim to use patterns for as many parts of the problem as possible, reducing the need to create entirely new approaches.
* The Process of Combining:
  * Combining patterns often involves including the key statements or instructions from each relevant pattern in your prompt.
  * The order of these statements can sometimes be important (e.g., Ask for Input usually works best at the end).
  * While sometimes straightforward, combining patterns can occasionally require careful consideration of how the different instructions interact.
* Benefits of Combining Patterns:
  * Creates more powerful and effective prompts.
  * Allows for more complex and sophisticated interactions with LLMs.
  * Enables the tackling of multifaceted problems by addressing different aspects with specific patterns.
  * Provides a structured approach to prompt engineering for complex tasks.
* **Key Insight:** The key to advanced prompt engineering lies in the ability to strategically combine multiple prompting patterns to address different facets of a problem, leading to more robust and effective solutions.
  * Think of patterns as building blocks that can be assembled in various ways.
  * Pay attention to how different patterns can complement each other.
  * By combining patterns, you can create prompts with greater depth and power.

### Outline Expansion Pattern

* Outline Expansion Pattern:
  * This pattern helps overcome the input and output limitations of LLMs by enabling the generation of large pieces of work in smaller, manageable sections.
  * It involves creating an outline of the desired output and then iteratively expanding specific points within that outline.
  * This allows for a structured approach to generating lengthy content, software, or other complex outputs.
* Rationale:
  * LLMs have limits on prompt size, conversation length, and output length.
  * Generating large works (e.g., books, extensive code) at once is often not feasible.
  * Outlines provide a roadmap and structure for breaking down large tasks into smaller, more manageable parts.
* Implementation:
  * Start by prompting the LLM to generate a bullet point outline for the desired topic.
  * The LLM acts as an "outline expander."
  * The user then selects a specific bullet point from the outline and asks the LLM to expand on it, creating a more detailed sub-outline or content.
  * This process can be repeated, expanding different parts of the outline to the desired level of granularity.
  * The Ask for Input and Persona patterns can be combined with this pattern.
* Example:
  * `Act as an outline expander. Generate a bullet point outline based on the input that I give you and then ask me for which bullet point you should expand on. Each bullet can have at most 3-5 sub bullets. The bullets should be numbered using the pattern [A-Z].[i-v].[* through ****]. Create a new outline for the bullet point that I select.  At the end, ask me for what bullet point to expand next. Ask me for what to outline.`
* Benefits:
  * Enables the generation of large and complex outputs that would exceed LLM limitations if attempted at once.
  * Provides a clear structure for the final output, making assembly easier.
  * Allows for focused generation on specific sections while maintaining an overview of the whole.
  * The outline can be used to provide context to the LLM when expanding specific points, especially if the conversation has become lengthy.
  * Example: Creating an outline for a book, then expanding each chapter or section individually.
* Key Considerations:
  * While the outline structure helps with assembly, it's crucial to ensure that individual expanded sections remain cohesive with the overall work and have the necessary context from other parts of the outline.
  * Cutting and pasting relevant parts of the outline back into the prompt can help maintain context as the outline expands.
  * This pattern works best for projects that can be naturally structured in an outline format.
* **Key Insight:** The outline expansion pattern offers a practical strategy for generating large-scale content or complex projects with LLMs by breaking them down into a hierarchical structure that can be developed iteratively, overcoming input/output limitations and providing a clear roadmap for assembly.
  * This method allows for focused work on smaller parts while maintaining a view of the whole.
  * The outline itself serves as a form of long-term memory and context.
  * It's a powerful technique for tackling ambitious projects with LLMs.

```text
> User
Act as an outline expander. Generate a bullet point outline based on the input that I give you and then ask me for which bullet point you should expand on. Create a new outline for the bullet point that I select. At the end, ask me for what bullet point to expand next.

Ask me for what to outline.

> ChatGPT
Sure, I'd be happy to help you with that! Please provide me with the topic or subject that you would like me to create an outline for.

> User
Writing effective prompts for ChatGPT

> ChatGPT
Great! Here's a bullet point outline for "Writing Effective Prompts for ChatGPT":

1. Introduction to ChatGPT
  - What is ChatGPT?
  - Applications of ChatGPT
2. Understanding the Importance of Prompts
  - Role of prompts in guiding ChatGPT's responses
  - Common challenges in prompt writing
3. Tips for Writing Effective Prompts
  - Clarity and specificity
  - Experimenting with different prompt styles
  - Using context and examples
4. Common Pitfalls to Avoid
  - Ambiguous or vague prompts
  - Overloading the prompt with information
  - Misaligned expectations
5. Testing and Refining Prompts
  - Iterative process of prompt testing
  - Analyzing and interpreting ChatGPT's responses
  - Making adjustments to improve prompt effectiveness
6. Conclusion
  - Recap of key points
  - Final thoughts on prompt writing for ChatGPT

Please let me know which bullet point you would like me to expand on, and I will create a new outline for that section.

> User
3.

> ChatGPT
Certainly! Here's a more detailed outline for the section "3. Tips for Writing Effective Prompts":

3. Tips for Writing Effective Prompts
  3.1. Achieving Clarity and Specificity
    - The importance of clear and specific language
    - Techniques for making prompts unambiguous
  3.2. Experimenting with Different Prompt Styles
    - Types of prompts (eg, questions, statements, scenarios)
    - Pros and cons of different prompt styles
    - When to use each style
  3.3. Providing Context and Examples
    - Using context to guide the model's understanding
    - Incorporating examples to illustrate desired responses
  3.4. Balancing Brevity and Detail
    - Striking the right balance between concise and informative prompts
    - Avoiding information overload while providing necessary details
  3.5. Setting the Tone and Style
    - Matching the tone and style to the desired output (e.g., formal, casual)
    - How tone and style influence the model's responses

Please let me know which sub-bullet point you would like me to expand on next, and I will create a new outline for that subsection.

> User
3.2

> ChatGPT
Sure! Here's a more detailed outline for the subsection "3.2 Experimenting with Different Prompt Styles":

3.2. Experimenting with Different Prompt Styles
  3.2.1. Types of Prompts
    - Question-based prompts
    - Statement-based prompts
    - Scenario-based prompts
    - Instruction-based prompts
  3.2.2. Pros and Cons of Different Prompt Styles
    - Advantages of question-based prompts
    - Limitations of question-based prompts
    - Advantages of statement-based prompts
    - Limitations of statement-based prompts
    - Advantages of scenario-based prompt
    - Limitations of scenario-based prompts
    - Advantages of instruction-based prompts
    - Limitations of instruction-based prompts
  3.2.3. Choosing the Right Style for Your Use Case
    - Factors to consider when selecting a prompt style
    - Matching the prompt style to the desired outcome
    - Experimenting with multiple styles to find the best fit

Please let me know which sub-bullet point you would like me to expand on next, and I will create a new outline for that subsection.
```

### Menu Actions Pattern

* Menu Actions Pattern:
  * This pattern involves defining a set of actions (essentially pre-defined prompts) within a conversation with an LLM that can be triggered by typing specific keywords or phrases.
  * It creates a "menu" of operations that can be easily reused without having to rewrite full prompts repeatedly.
  * This is particularly useful for long conversations or when performing the same tasks multiple times.
* Rationale:
  * Simplifies repetitive tasks by codifying actions.
  * Improves efficiency by allowing users to trigger complex operations with short commands.
  * Facilitates consistency in how certain tasks are performed.
  * Enables the creation of interactive "programs" within a prompt.
  * Allows for sharing and reuse of helpful prompts or actions.
* Implementation:
  * Describe the keyword or phrase that will trigger each action.
  * Clearly define what the LLM should do when each keyword/phrase is used, including any placeholders for user input.
  * The "menu" of actions is typically defined at the beginning of the conversation.
  * Users can then invoke these actions later in the conversation by typing the defined keywords and providing any necessary input.
* Example:
  * `Whenever I type: "add FOOD", you will add FOOD to my grocery list and update my estimated grocery bill. Whenever I type "remove FOOD", you will remove FOOD from my grocery list and update my estimated grocery bill. Whenever I type "save" you will list alternatives to my added FOOD to save money. At the end, you will ask me for the next action. Ask me for the first action.`
* Benefits:
  * Enhances efficiency by avoiding the need to rephrase complex prompts.
  * Promotes consistency in the execution of specific tasks.
  * Allows for rapid iteration and manipulation of LLM output.
  * Facilitates the creation of personal "programs" within a conversation.
  * Enables sharing of useful actions within teams or organisations.
  * Reduces the need to remember exact phrasing for frequently used prompts.
  * Can be used to codify best practices into reusable actions.
  * Useful for creating structured interactions in applications like customer service portals.
* Key Considerations:
  * The keywords or phrases used to trigger actions should be distinct and easy to remember.
  * The definition of each action should be clear and unambiguous.
  * This pattern is most beneficial for tasks that are performed repeatedly within a conversation.
* **Key Insight:** The menu actions pattern transforms a text-based conversation with an LLM into a more interactive and efficient experience by allowing users to define and reuse specific operations through simple keywords, streamlining workflows and promoting consistency.
  * It enables the creation of a personalised set of tools within a prompt.
  * It facilitates sharing and standardisation of effective prompts.
  * It simplifies complex interactions by abstracting away the need for lengthy prompts.

```text
> User
Whenever I type: "write <Bullet Point> <Paragraphs>", you will write content for the selected bullet point <Bullet Point>. You will write <Paragraphs> of text. Whenever I type just "<Bullet Point>" you will expand that bullet point. At the end, you will ask me for the next action.

> ChatGPT
Understood! Please provide me with the specific bullet point you would like me to write content for, along with the number of paragraphs you would like me to write. Alternatively, you can provide just the bullet point if you would like me to expand on it and create a new outline. After completing the requested action, I will ask you for the next action.

> User
write 3.5.3 2

> ChatGPT
3.5.3. Experimenting with Tone and Style Variations

When crafting prompts for language models like ChatGPT, experimenting with variations in tone and style can be a valuable exercise. Tone refers to [...]

The process of experimenting with tone and style variations begins with creating multiple versions of the same prompt, [...]

What would you like me to do next? Please provide me with the specific bullet point you would like me to write content for, along with the number of paragraphs you would like me to write. Alternatively, you can provide just bullet point if you would like me to expand on it and create a new outline.

> User
3.5.2

> ChatGPT
Here's a more detailed outline for the subsection "3.5.2. Matching Tone and Style to Desired Output":

3.5.2. Matching Tone and Style to Desired Output
  3.5.2.1. Considerations for Choosing the Appropriate Tone
    - Assessing the target audience and their preferences
    - Determining the purpose of the communication (eg, inform, persuade, entertain)
    - Aligning the tone with the context of the interaction
  3.5.2.2. Considerations for Choosing the Appropriate Style
    - Deciding on the level of formality (e.g., formal, informal)
    - Selecting a style that matches the content (e.g., technical, creative)
    - Ensuring consistency in style throughout the interaction
  3.5.2.3. Examples of Tone and Style for Different Use Cases
  - Tone and style for customer support interactions
  - Tone and style for creative writing projects
  - Tone and style for technical documentation
  - Tone and style for instructional content

Please let me know which sub-bullet point you would like me to expand on next, and I will create a new outline for that subsection. Alternatively, you can provide me with the specific sub-bullet point you would like me to write content for, along with the number of paragraphs you would like me to write.

> User
text 3.5.2.3 1

> ChatGPT
3.5.2.3. Examples of Tone and Style for Different User Cases

The tone and style of a prompt can vary significantly depending on the specific use case and desired outcome. For example, in customer support interactions, the tone is often friendly and helpful [...]
```

### Fact Check List Pattern

* Fact Checklist Prompting Pattern:
  * This pattern involves prompting the LLM to generate a list of the underlying facts presented in its output.
  * This checklist helps users identify key pieces of information that need to be verified for accuracy.
  * It encourages users to fact-check the LLM's output and take ownership of its correctness.
* Rationale:
  * LLMs are text generators and can produce outputs that appear factual but may contain inaccuracies or falsehoods.
  * The realistic and convincing nature of the output can lead users to assume its truthfulness without verification.
  * The fact checklist pattern provides a structured way to identify and follow up on the factual claims made by the LLM.
* Implementation:
  * Instruct the LLM that whenever it generates text, it should also produce a list of the fundamental facts contained within that text.
  * These facts should be presented somewhere in the output, e.g., at the end.
  * The facts listed should be crucial to the veracity of the output; if any are incorrect, the overall output's accuracy is undermined.
* Benefits:
  * Provides a clear list of specific claims to fact-check, rather than requiring the user to manually extract them from potentially large amounts of text.
  * Encourages a habit of verifying LLM output.
  * Allows users to compare the generated fact list against the original text to ensure completeness of fact extraction.
  * Sets a minimum standard for verification – users should at least check the listed facts.
  * Helps users become more aware of the assumptions and factual basis of the LLM's output.
* Key Considerations:
  * The fact checklist doesn't guarantee complete accuracy, as there might be unlisted assumptions or subtle inaccuracies.
  * Users still need to use external sources and their own knowledge to verify the listed facts.
  * Comparing the fact list to the original text is important to identify any potentially overlooked factual claims.
* **Key Insight:** The fact checklist prompting pattern serves as a valuable tool for promoting critical evaluation of LLM output by explicitly highlighting the underlying factual claims, thereby encouraging users to engage in necessary fact-checking and take responsibility for the accuracy of the information.
  * It shifts the user from passive consumption of LLM output to active verification.
  * It provides a tangible starting point for the fact-checking process.
  * While not a foolproof method, it significantly improves the likelihood of identifying and correcting inaccuracies.

```text
> User
Whenever you output text, generate a set of facts that are contained in the output. The set of facts should be inserted at the end of the output. The set of facts should be the fundamental facts that could undermine the veracity of the output if any of them are incorrect.

> ChatGPT
Understood! Whenever I output text, I will generate a set of fundamental facts contained in the output and insert them at the end of the output. These facts are essential for the veracity of the output, and their accuracy is important for the overall credibility of the content.

[...]

> User
text 3.5.2.2 1

> ChatGPT
3.5.2.2. Considerations for Choosing the Appropriate Style

When crafting prompts for language models, it's important to consider the appropriate writing style that matches the content being conveyed. The style of writing can range from technical and precise to creative and expressive, or instructional and informative. The choice of style should be influenced by factors such as the type of content, the intended audience, and the purpose of the communication. For example, technical documentation may require a formal and precise style to convey complex information accurately, while creative writing projects [...]

[Set of Fundamental Facts:

1. Writing style can range from technical to creative to instructional.
2. The choice of writing style should be influenced by factors such as content type, audience, and communication purpose.
3. Technical documentation often requires a formal and precise style.
4. Creative writing projects may be Regenerate response and imaginative style.
5. [...]
6. [...]]

[...]
```

```text
> User
When you next output an answer, generate a set of facts that are contained in the answer. The set of facts should be numbered and inserted at the end of the answer. The set of facts should be the fundamental facts that could undermine the veracity of the answer if any of them are incorrect. The answer should have an indication in the form [NUMBER] in places that correspond to the numbered facts.
Write 2 paragraphs on the effects of Likert Bias.

> ChatGPT
Likert bias, also known as response style bias, refers to the tendency of respondents to answer Likert-scale questions in a patterned or skewed way, rather than providing responses that truly reflect their thoughts or feelings. One common form is central tendency bias, where individuals avoid extreme responses and consistently select the middle options, potentially masking strong opinions or attitudes [1]. Another form is acquiescence bias, in which respondents tend to agree with statements regardless of content, especially when unsure or fatigued [2]. These patterns can distort the validity of survey data, leading to inaccurate conclusions about public opinion, employee satisfaction, or consumer preferences [3].

The effects of Likert bias can be significant in both academic research and applied settings. When responses cluster artificially due to bias rather than true attitudes, it becomes difficult to distinguish between groups or detect meaningful trends over time [4]. For example, in workplace surveys, Likert bias may lead managers to believe employee morale is stable or positive, when in fact nuanced concerns are being masked by neutral or agreeable responses [5]. This undermines the reliability of data-driven decision-making and can result in misguided policy or strategic actions based on flawed interpretations [6].

---

Set of Fundamental Facts

1. Central tendency bias causes respondents to avoid extreme options on Likert scales.
2. Acquiescence bias leads people to agree with statements regardless of content.
3. Likert bias distorts survey results, affecting their validity.
4. Biased response patterns hinder accurate detection of attitudinal trends.
5. Likert bias can obscure real concerns in organizational or social research.
6. Decisions based on biased data may be flawed or misinformed.
```

### Tail Generation Pattern

* Tail Generation Prompting Pattern:
  * This pattern involves instructing the LLM to generate a "tail" at the end of its output that reminds it of the ongoing task, rules, or context of the conversation.
  * The tail serves as a way to reinforce the initial instructions and prevent the LLM from forgetting them over a long conversation.
  * This is particularly useful for maintaining consistency and adherence to rules in extended interactions.
* Rationale:
  * LLMs have a limited context window and can sometimes forget earlier instructions or the overall goal of a long conversation.
  * Regularly reminding the LLM of the rules or task helps maintain focus and consistency in its responses.
  * The tail generation pattern automates this reminder process.
* Implementation:
  * In the initial prompt, instruct the LLM to generate a specific "tail" at the end of each of its outputs.
  * The tail should reiterate key aspects of the task, rules, or ask for the next input related to the ongoing objective.
  * This can be combined with other patterns like Alternative Approaches and Ask for Input.
  * Example: Instructing the LLM to always end its response with "Please ask me for the next prompt to create alternatives for."
* Benefits:
  * Helps maintain the LLM's memory of the conversation's context and rules over longer interactions.
  * Reduces the likelihood of the LLM deviating from the intended task or forgetting specific instructions.
  * Automates the process of re-introducing important information into the conversation.
  * Improves the consistency and coherence of the LLM's responses in extended dialogues.
* Key Considerations:
  * The content of the tail should be concise but effectively reiterate the key information.
  * The tail should be consistently generated at the end of each LLM output.
  * This pattern is most beneficial for longer, multi-turn conversations where maintaining context is crucial.
* **Key Insight:** The tail generation prompting pattern provides a simple yet effective mechanism for reinforcing instructions and maintaining context in long conversations with LLMs by appending a reminder "tail" to each of its responses, thereby improving consistency and adherence to the desired task or rules.
  * It acts as a form of continuous prompting, keeping the LLM aligned with the user's goals.
  * It is particularly valuable when specific behaviours or rules need to be maintained throughout an extended interaction.
  * By automating the reminder, it reduces the need for the user to manually reiterate instructions.

```text
> User
Whenever I ask you to write a prompt for me to accomplish a task, list what the task is, list alternative approaches for completing the task, and then write a prompt for yourself for each approach. When you are done, ask me for the next prompt to create alternatives for.

Ask me what I want you to write a prompt for.

> ChatGPT
Certainly! What task would you like me to write a prompt for?

> User
Write a prompt for ChatGPT to automatically detect questions in a chain of emails and summarize everyone's opinion on the questions as bullet points beneath each question.

> ChatGPT
Task: Write a prompt for ChatGPT to automatically detect questions in a chain of emails and summarize everyone's opinion on the questions as bullet points beneath each question.

Alternative Approaches:

1. Approach 1: [...]

Please let me know if you have another task for which you'd like me to write a prompt and create alternative approaches.

> User
Write a prompt to evaluate several different prompts for summarizing the questions in an email conversation and the different stakeholders' perspectives on the questions.

> ChatGPT
[...]
Please let me know if you have another task for which you'd like me to write a prompt and create alternative approaches.
```

### Semantic Filter Pattern

* Semantic Filter Prompting Pattern:
  * This pattern involves instructing the LLM to act as a filter, taking in text and removing or keeping information based on its meaning or specified qualities.
  * It allows for the manipulation of text based on semantic understanding rather than just keyword matching.
  * This is useful for tasks like removing sensitive information, redacting text, or extracting specific types of content.
* Rationale:
  * LLMs excel at understanding the meaning of text.
  * This pattern leverages that ability to selectively remove or retain information based on its semantic content.
  * It provides a more sophisticated way to process text compared to simple keyword-based filtering.
* Implementation:
  * Clearly instruct the LLM to "filter this information."
  * Provide semantic rules or criteria for what should be removed or kept (e.g., "remove all dates," "remove any information that indicates the patient has diabetes").
  * You can also instruct the LLM to rewrite the text minimally to address any awkwardness caused by the removals.
* Format of the Semantic Filter Pattern:
  * To use this pattern, your prompt should make the following fundamental contextual statements:
    * `Filter this information to remove X`
  * You will need to replace "X" with an appropriate definition of what you want to remove, such as. "names and dates" or "costs greater than $100".
  * Examples:
    * `Filter this information to remove any personally identifying information or information that could potentially be used to re-identify the person.`
    * `Filter this email to remove redundant information.`
* Benefits:
  * Enables filtering of text based on meaning and context, rather than just keywords.
  * Can be used to remove sensitive or confidential information.
  * Useful for redacting text while preserving the overall meaning.
  * Can help in extracting specific types of information based on their semantic content.
* Key Considerations:
  * The accuracy of the filter depends on the LLM's understanding of the semantic rules provided.
  * LLMs are not always perfect and may not catch every instance of the targeted information.
  * For critical applications like privacy protection, this pattern should be used as part of a multi-layered security approach and not as the sole method of filtering.
  * The LLM's responses can have some randomness, so the filtering might not be perfectly repeatable.
* **Key Insight:** The semantic filter prompting pattern harnesses the LLM's language understanding capabilities to selectively remove or retain information from text based on its meaning, offering a powerful tool for text manipulation in various applications, although it should be used with caution and as part of a broader strategy for critical tasks.
  * It allows for more intelligent text processing than simple keyword filters.
  * It can be a valuable component in data sanitization and information extraction workflows.
  * However, its limitations and potential for errors necessitate careful implementation and supplementary checks.

```text
> User
Filter this information to remove all dates and rewrite the text as little as possible to fix the issues caused by the date removals.

Vanderbilt University (informally Vandy or VU) is a private research university in Nashville, Tennessee. Founded in 1873, it was named in honor of shipping and rail magnate Cornelius Vanderbilt, [...]

The university comprises ten schools and enrolls approximately 13,800 students from the US and over 100 foreign countries. [...] Vanderbilt University Medical Center, formerly part of the university, became a separate institution in 2016. With the exception of the off-campus observatory, [...]

The Fugitives and Southern Agrarians were based at the university in the first half of the 20th century and helped revive Southern literature among others. [...]

> ChatGPT
Vanderbilt University (informally Vandy or VU) is a private research university in Nashville, Tennessee. Founded in the 19th century, it was named in honor of shipping and rail magnate Cornelius Vanderbilt, [...]

The university comprises ten schools and enrolls approximately 13,800 students from the US and over 100 foreign countries. Vanderbilt University Medical Center, formerly part of the university, became a separate institution in the 21st century. With the exception of the off-campus observatory [...]

The Fugitives and Southern Agrarians were based at the university in the first half of the 20th century and helped revive Southern literature among others. [...]

> User
Filter the information below to remove any information that would help someone figure out that the patient has diabetes. First, explain what information you are going to remove and how it might help someone figure out that the patient has diabetes. Then, provide the filtered information.

Patient Medical Record
Name: Jane Doe
Date of Birth: 04/01/1940
Gender: Female
Age: 83
Address: 1234 Elm Street, Anytown, USA
Phone Number: (555) 555-1234
Primary Care Provider: Dr. John Smith
Date of Visit: 04/15/2023

Chief Complaint:
The patient presents to the clinic with complaints of increased thirst and fatigue for the past two weeks.

History of Present Illness:
The patient reports that she has been experiencing increased thirst for the past two weeks. She has also been feeling more fatigued than usual. She denies any recent weight loss, blurry vision, or infections. She has not checked her blood glucose levels at home recently.

Past Medical History:
Type 2 diabetes mellitus (diagnosed 15 years ago)
Hypertension
Hyperlipidemia
Osteoarthritis of the knees

Medications:
Metformin 1000 mg twice daily
Lisinopril 10 mg daily
Atorvastatin 20 mg daily
Acetaminophen as needed for pain

Allergies:
Penicillin (causes rash)

> ChatGPT
Information to be removed and why:

1. The chief complaint of "increased thirst and fatigue" should be removed because increased thirst (polydipsia) is a common symptom of diabetes.
2. The history of present illness mentions "increased thirst" and "not checked her blood glucose levels, both of which should be removed because they are related to diabetes symptoms and management.
3. The past medical history Includes "Type 2 diabetes mellitus (diagnosed 15 years ago)," which should be removed because it directly indicates that the patient has diabetes.
4. The medication "Metformin 1000 mg twice daily" should be removed because metformin is a medication commonly used to manage diabetes.

Filtered Information:

Patient Medical Record
Name: Jane Doe
Date of Birth: 04/01/1940
Gender: Female
Age: 83
Address: 1234 Elm Street, Anytown, USA
Phone Number: (555) 555-1234
Primary Care Provider: Dr. John Sm
Date of Visit: 04/15/2023

Chief Complaint:
The patient presents to the clinic with complaints of fatigue for the past two weeks.

History of Present Illness:
The patient reports that she has been feeling more fatigued than usual. She denies any recent weight loss, blurry vision, or infections.

Past Medical History:
Hypertension
Hyperlipidemia
Osteoarthritis of the knees

Medications:
Lisinopril 10 mg daily
Atorvastatin 20 mg daily
Acetaminophen as needed for pain

Allergies:
Penicillin (causes rash)
```
