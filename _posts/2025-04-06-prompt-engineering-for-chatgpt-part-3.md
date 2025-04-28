---
layout: post
title: Prompt Engineering for ChatGPT Part 3
categories: ai llm
published: true
plantuml: false
---

Summary of the [Prompt Engineering for ChatGPT course at Coursera](https://www.coursera.org/learn/prompt-engineering/), part 3 of 4, covering Game Play Pattern, Template Pattern, Meta Language Creation Pattern, Recipe Pattern, and Alternative Approaches Pattern.

* **Game Play Pattern**
  * To create a game around a given topic.
  * `Create a game for me around the topic of cybersecurity. The game should involve identifying potential security risks in a given piece of code.`
  * `Create a trivia game for me around the topic of world history. The game should involve answering questions about different historical events.`
* **Template Pattern**
  * To structure the LLM output in a desired format, similar to giving an assistant a form letter with placeholders to fill in.
  * `I am going to give you a template for your output. CAPITALIZED WORDS are my placeholders. Fill in my placeholders with your output. Please preserve the overall formatting of my template. My template is: Bio: <NAME>; Executive Summary: <ONE SENTENCE SUMMARY>. Extract information about the people in the following: ...`
* **Meta Language Creation Pattern**
  * To create a new language or vocabulary for interaction with the LLM.
  * `Whenever I say 'generate a report', I want you to create a summary of the most important points we've discussed.`
  * `Whenever I say 'tell me a story', I want you to create a short narrative based on the topic we're discussing.`
  * `When I say "variations(<something>)", I mean give me ten different variations of <something>`
* **Recipe Pattern**
  * To get the LLM to generate a sequence of steps or a procedure for achieving a certain goal.
  * `I would like to deploy a web application to AWS using Docker containers and Ansible. I know that I need to create a Dockerfile, write an Ansible playbook, and configure AWS. Provide a complete sequence of steps for me.`
  * `I would like to bake a chocolate cake. I know that I need flour, sugar, cocoa powder, and eggs. Provide a complete sequence of steps for me.`
* **Alternative Approaches Pattern**
  * To get the LLM to provide alternative ways of accomplishing a task.
  * `Whenever I ask you to deploy an application to a specific cloud service, if there are alternative services to accomplish the same thing with the same cloud service provider, list the best alternative services and then compare/contrast the pros and cons of each approach.`
  * `Whenever I ask you for a workout routine, if there are alternative exercises to accomplish the same fitness goal, list the best alternate exercises and then compare/contrast the pros and cons of each approach.`

_The following summary is mostly generated using ChatGPT and Gemini based on the course transcript, while the examples are mostly copied from the course itself._

---

* [Prompt Patterns II](#prompt-patterns-ii)
  * [Game Play Pattern](#game-play-pattern)
  * [Template Pattern](#template-pattern)
  * [Meta Language Creation Pattern](#meta-language-creation-pattern)
  * [Recipe Pattern](#recipe-pattern)
  * [Alternative Approaches Pattern](#alternative-approaches-pattern)

## Prompt Patterns II

### Game Play Pattern

* Game Play Prompting Pattern:
  * This pattern uses LLMs to create and manage games, providing a fun and engaging way to learn or practice skills.
  * The LLM acts as a game master, generating rules, tasks, and feedback.
  * This is a very useful pattern for learning new skills.
* Rationale:
  * Games can make learning more enjoyable and effective.
  * LLMs can leverage their training data to create diverse and challenging game content.
  * This pattern allows for interactive and personalised learning experiences.
* Implementation:
  * Instruct the LLM to "play a game involving [topic]."
  * Define the basic rules and structure of the game.
  * The LLM will generate tasks, provide feedback, and manage the gameplay.
  * The user can also provide specific instructions about the type of game that they wish to play.
* Benefits:
  * Enhances learning through interactive and engaging gameplay.
  * Provides personalised challenges and feedback.
  * Leverages the LLM's knowledge to generate diverse game content.
  * Example: Creating a game to improve prompt engineering skills, where the LLM provides tasks and evaluates the user's prompts.
* Key Considerations:
  * The quality of the game depends on the clarity of the rules and instructions.
  * The LLM can generate diverse content, but user input can refine the game's focus.
  * It is possible to use this pattern to learn any subject.
* **Key Insight:** The game play prompting pattern transforms LLMs into interactive learning tools, making skill development fun and engaging.
  * This approach leverages the LLM's ability to create dynamic content and provide personalised feedback.
  * This pattern is very useful for practising prompt engineering.
  * This pattern allows for the creation of very engaging learning experiences.

```text
> User
We are going to play a game involving prompt engineering. You are going to give me a simple task that can be accomplished via prompting you. You tasks should all have a reasoning or programming component to them, although they shouldn't require creating source code.

I will try to write a prompt for you to solve the task. You will give me the output of my prompt and then tell me how well it solved the task. Ask me questions until I tell you to stop. You will ask me a question, wait for my response, and then ask me another question after telling me how well I did.

Ask me the first question.

> ChatGPT
Great! Let's get started with the first task:

Task: Given a list of numbers, determine whether the list contains any duplicate elements. If it does, return "Yes, there are duplicates." If it does not, return "No duplicates found."

Please write a prompt for me to solve this task.

> User
Numbers: 1, 2, 3
Duplicates? No duplicates found.
Numbers: 2, 2, 2
Duplicates? Yes there are duplicates.
Numbers: 2, 3, 4, 2
Duplicates? Yes there are duplicates.
Numbers: 100, 10000, 1000000
Duplicates?

> ChatGPT
No duplicates found.

Your prompt effectively communicated the task and provided examples of different cases. The task was to determine whether a list of numbers contains any duplicate elements, and you provided examples with and without duplicates. Based on your prompt, I was able to correctly determine that hte list "100, 10000, 100000" does not contain any duplicate elements, and I provided the correct response "No duplicates found."

Let's move on to the next task:

Task: Given a sentence, count the number of words in the sentence and return the result in the format "The sentence contains X words," where X is the number of words.

Please write a prompt for me to solve this task.

> User
I am going to give you a template for your output. NUMBER is my placeholder. Fill in my placeholder with your output. Please preserve the overall formatting of my template. My template is "The sentence contains NUMBER words."

How many words are in the following sentence: "The cat jumped on the mat."

> ChatGPT
The sentence contains 6 words.

Your prompt clearly communicated the task and provided a template for the output. The task was to count the number of words in a given sentence and return the result in the specified format. Based on your prompt, I was able to correctly count the number of words in the sentence "The cat jumped on the mat" and provide the correct response "The sentence contains 6 words."

Let's move on to the next task:

Task: Given a date in the format "YYYY-MM-DD," determine whether the year is a leap year or not. If it is a leap year, return "The year YYYY is a leap year." If it is not a leap year, return "The year YYYY is not a leap year. Replace "YYYY" with the actual year.

Please write a prompt of me to solve this task.

> User
Date: 2000-01-01
Leap Year? The year 2000 is a leap year.
Date: 2004-05-18
Leap Year? The year 2004 is a leap year.
Date: 2009-07-04
Leap Year? The year 2004 is not a leap year.
Date: 2023-04-12
Leap Year?

> ChatGPT
The year 2023 is not a leap year.

Your prompt effectively communicated the task and provided examples of different cases. The task was to determine whether a given year (extracted from a date in the format "YYYY-MM-DD") is a leap year or not, and you provided examples of both leap years and non-leap years. Based on your prompt, I was able to correctly determine that the year 2023 is not a leap year, and I provided the correct response "The year 2023 is not a leap year."

Note: There is a small typo in the third example ("The year 2004 is not a leap year" should be "The year 2009 is not a leap year"), but this did not affect my ability to understand and respond to the task.

Let's move on to another task:

[...]
```

```text
> User
We are going to play a game involving prompt engineering. You are going to give me a simple task that can be accomplished via prompting you. Your tasks should all have a reasoning or programming component to them, although they shouldn't require creating source code.

I will try to write a prompt for you to solve the task. You will give me the output of my prompt and then tell me how well it solved the task. Ask me questions until I tell you to stop. You will ask me a question, wait for my response, and then ask me another question after telling me how well I did.

All of your questions should revolve around the "Recipe Prompt Pattern". This pattern provides constraints to ultimately output a sequence of steps given some partially provided "Ingredients" that must be configured in a sequence of steps to achieve a stated goal. The pattern is not about cooking per se, but creating a complete sequence of steps to achieve a goal given an incomplete list of intermediate steps.

Ask me the first question.

> ChatGPT
Great! Let's get started with the first task for the "Recipe Prompt Pattern" game.

Task 1: Your goal is to create a prompt that instructs me to generate a sequence of steps for assembling a simple wooden bookshelf. The bookshelf has four main components: the top and bottom panels, the side panels, and the shelves. You have been provided with the following "Ingredients" (intermediate steps):

- Attach the top panel to the side panels.
- Insert the shelves into the designated slots.

Using these intermediate steps, create a prompt that will result in a complete sequence of steps for assembling the bookshelf. Remember, the prompt should be designed to fill in any missing steps and provide a clear order for completing the assembly.

> User
We are going to change the topic of your questions. The topic is now: The Context Manager Pattern

1) Intent and Context: The intent of this pattern is to enable users to specify or remove context for a conversation with an LLM. The goal is to focus the conversation on specific topics or exclude unrelated topics from consideration. This pattern gives users greater control over what statements the LLM considers or ignores when generating output.

Ask me the first question.

> ChatGPT
Certainly! Let's get started with the first task for the "Context Manager Pattern" game.

Task 1: Your goal is to create a prompt that instructs me to provide information about the history of the Eiffel Tower. However, you want to ensure that the response is focused exclusively on the construction of the Eiffel Tower and does not include any information about events or incidents that occurred after its completion. In other words, you want to specify the context of the conversation to be limited to the construction period of the Eiffel Tower.

Using the Context Manager Pattern, create a prompt that will result in a response that adheres to the specified context. Remember, the prompt should be designed to focus the conversation on the construction of the Eiffel Tower and exclude any unrelated topics or events that happened after its completion.
```

### Template Pattern

* Purpose of the Template Pattern
  * Helps structure the output of large language models in a desired format.
  * Similar to giving an assistant a form letter with placeholders to fill in.
* How It Works
  * The user provides a template with placeholders.
  * ChatGPT replaces the placeholders with relevant content while preserving the template's structure.
  * Capitalised words indicate placeholders for the model to replace.
  * Markdown can be used to format the output effectively.
* Example 1: Generating Questions and Answers
  * A template was created with sections labelled along with placeholders:
    * `***Question:*** QUESTION`
    * `***Answer:*** ANSWER`
  * The user provided content on Paleo-Indians from Wikipedia, along with instructions to generate 20 questions in the specified format.
  * ChatGPT generated 20 formatted questions and answers following the template.
* Example 2: Researching a Person (Doug Schmidt)
  * Used ChatGPT to generate 20 questions about Doug Schmidt based on available web data.
  * If web data is outdated, pasting direct information would be more reliable.
  * The template pattern ensured consistent formatting of the questions.
* Example 3: Extracting and Summarising Historical Figures
  * A template was created with placeholders.
  * Constraints were set in the placeholders:
    * `## Bio: <NAME>`
    * `***Executive Summary:*** <ONE SENTENCE SUMMARY>`
    * `***Full Description:*** <ONE PARAGRAPH SUMMARY>`
  * ChatGPT successfully extracted names and summarised information while following these rules.
* **Key Insight:** Power and Flexibility of the Template Pattern
  * Ensures Consistency
    * Maintains strict formatting and structure in responses.
  * Enables Intelligent Extraction
    * Can identify key elements (e.g., people, roles) from unstructured data.
  * Supports Complex Rules
    * Placeholders can include constraints, such as requiring summaries of specific lengths.
  * Saves Time
    * Automates time-consuming tasks like summarisation and structured data extraction.
  * Improves Accuracy
    * Reduces model-generated variations and aligns outputs with user-defined expectations.

```text
> User
I am going to give you a template for your output. CAPITALIZED WORDS are my placeholders. Fill in my placeholders with your output. Please preserve the overall formatting of my template. My template is:

***Question**** QUESTION
***Answer:*** ANSWER

I will give you the data to format in the next prompt. Create twenty questions using my template.

> ChatGPT
Of course! Please provide the data you would like me to use to create the twenty questions using your template. Once I have the data, I will format it according to the template you provided.

> User
Paleo-Indians, Paleoindians or Paleo-Americans were the first peoples who entered, and subsequently inhabited, the Americas during the final glacial episodes of the late Pleistocene period. The prefix paleo- comes from the Greek adjective palaios [...]

> ChatGPT
Question: WHO WERE THE PALEO-INDIANS?
Answer: Paleo-Indians, also known as Paleoindians or Paleo-Americans, were the first peoples who entered, and subsequently inhabited, the Americas during the final glacial episodes of the late Pleistocene period.

Question: WHAT DOES THE PREFIX "PALEO-" MEAN?
Answer: The prefix "paleo-" comes from the Greek adjective "palaios" [...]

> User
Using the content here: https://www.dre.vanderbilt.edu/~schmidt/resume.html create twenty questions.

> ChatGPT
As of my knowledge cutoff date in September 2021, the content of the webpage provided may have been different from its current state. Therefore, I will generate questions based on the content available on the webpage as of my knowledge cutoff date. If the content has changed since then, please let me know, and I can adjust the questions accordingly.

Question: WHAT IS THE NAME OF THE INDIVIDUAL WHOSE RESUME IS PRESENTED ON THE WEBPAGE?
Answer: The name of the individual whose resume is presented on the webpage is Dr. Douglas C. Schmidt.

Question: WHAT IS DR. DOUGLAS C. SCHMIDT'S CURRENT POSITION?
Answer: As of the knowledge cutoff date in September 2021, Dr. Douglas C. Schmidt's current position is Cornelius Vanderbilt Professor of Engineering at Vanderbilt University.

[...]

> User
I am going to give you a template for your output. CAPITALIZED WORDS are my placeholders. Fill in my placeholders with your output. Please preserve the overall formatting of my template. My template is:

## Bio: <NAME>
***Executive Summary:*** <ONE SENTENCE SUMMARY>
***Full Description:*** <ONE PARAGRAPH SUMMARY>

Extract information about the people involved in the history of Vanderbilt:

In the years before the American Civil War of 1861-1865, the Methodist Episcopal Church South had been considering the creation of a regional university for the training of ministers in a location central to its congregations.[18] Following lobbying by Nashville bishop Holland Nimmons McTyeire, church leaders voted to found "The Central University of the Methodist Episcopal Church, South" in Nashville in 1872. [18][19] However, lack of funds and the ravaged state of the Reconstruction Era South delayed the opening of the college. [18]

The following year, McTyeire stayed at the New York City residence of Cornelius Vanderbilt, whose second wife was Frank Armstrong Crawford Vanderbilt (1839-1885), a cousin of McTyeire's wife, Arnelia Townsend McTyeire (1827-1891); both women were from Mobile, Alabama [...]

> ChatGPT
Bio: Holland Nimmons McTyeire
Executive Summary: Holland Nimmons McTyeire was a Nashville bishop who played a key role in the founding of Vanderbilt University and served as the chairman of the Board of Trust for life.
Full Description: Holland Nimmons McTyeire was a bishop of the Methodist Episcopal Church South who lobbied for the creation of a regional university in Nashville, leading to the founding of "The Central University of the Methodist Episcopal Church, South" in 1872. [...]

Bio: Cornelius Vanderbilt
Executive Summary: Cornelius Vanderbilt was the wealthiest man in the United States and the benefactor of Vanderbilt University, which was named in his honor.
Full Description: Cornelius Vanderbilt was the wealthiest man in the United States during his time and had initially planned to establish a university on Staten Island, New York. However, [...]
```

### Meta Language Creation Pattern

* Natural Language Limitations
  * Writing everything in full sentences is not always the most efficient way to provide input to a large language model.
  * Many fields, like mathematics and note-taking, use shorthand or specialised languages for efficiency.
  * Communication in these languages works because both the sender and receiver understand the meaning of the symbols or shorthand.
* The Meta Language Creation Pattern
  * This pattern involves defining a new shorthand language for communication with the language model.
  * Users describe the meaning of symbols or statements, allowing the model to interpret the shorthand correctly.
  * Once trained on the shorthand, the model can respond to it accurately.
* General format:
  * To use this pattern, your prompt should make the following fundamental contextual statements: `When I say X, I mean Y (or would like you to do Y)`
  * You will need to replace `X` with an appropriate statement, symbol, word, etc. You will then need to map this to a meaning, `Y`.
  * Examples:
    * `When I say "variations(<something>)", I mean give me ten different variations of <something>`
    * Usage: `variations(company names for a company that sells software services for prompt engineering)`
    * Usage: `variations(a marketing slogan for pickles)`
* Example: Trip Planning Application
  * The user defines a shorthand notation for describing travel plans.
  * Example: `"Nashville,3 -> Memphis,2" means staying 3 days in Nashville and 2 days in Memphis.`
  * The model learns to interpret the shorthand and generate itineraries accordingly.
* Demonstrating the Pattern in Action
  * After defining the notation, the user can simply input `Nashville,0 -> Dallas,1 -> Granbury,4`, and the model understands:
    * No stay in Nashville
    * 1-day stay in Dallas
    * 4-day stay in Granbury
  * The model then generates appropriate itineraries for each stop.
* Benefits of Using a Meta Language
  * Saves time compared to writing full sentences.
  * Enables more precise and consistent input, reducing ambiguity.
  * Organisations can standardise shorthand notation to ensure uniform data entry and reasoning.
* **Key Insight:** Creating a structured shorthand allows users to efficiently communicate complex instructions.
  * Helps improve consistency, reducing variability in input.
  * Allows organisations to enforce standardised data entry.
  * Ensures the language model interprets input correctly, leading to better and more predictable results.

```text
> User
We are going to create a trip planning application. I will describe my trip and you will list interesting things to do in places that I will pass through. I will tell you how many days I will stay in each place and you will list possible itineraries.

To describe my route, I am going to use a shorthand notation.

When I say "Nashville,3->Memphis,2", I mean that my route will go from Nashville to Memphis and that I will stay 3 days in Nashville and 2 days in Memphis.

> ChatGPT
Got it! I'll provide you with a list of interesting things to do in each place you mention, along with possible itineraries based on the number of days you plan to stay in each location. Let's start with your example route: "Nashville,3->Memphis,2".

Nashville (3 days):

Nashville, also known as "Music City," is famous for its vibrant music scene, especially country music. Here are some interesting things to do and possible itineraries for your 3-day stay in Nashville:

Day 1: [...]

> User
Nashville,0->Dallas,1->GranburyTX,4

> ChatGPT
Surel Since you mentioned that you won't be spending any time in Nashville, I'll focus on providing you with interesting things to do and possible itineraries for your 1-day stay in Dallas and your 4-day stay in Granbury, Texas.

Dallas (1 day):
Dallas is a major city in Texas known for its modern architecture, cultural attractions, and vibrant arts scene. Here are some interesting things to do and a possible itinerary for your 1-day stay in Dallas:

Day 1:
- Visit The Sixth Floor Museum at Dealey Plaza to learn about the assassination of President John F. Kennedy.
- Explore the Dallas Museum of Art, which features a diverse collection of art from around the world.
[...]
```

### Recipe Pattern

* Partial Knowledge in Problem Solving
  * Often, users know only part of a solution when working with a large language model (LLM).
  * The LLM is used to "fill in the blanks" and complete the rest of the process.
* What is the Recipe Pattern?
  * A technique where users:
    * Provide the goal they want to achieve
    * Offer partial steps or known elements of a solution
    * Ask the LLM to complete the missing steps
  * Useful for filling gaps in a known process or series of actions.
* Natural Use of Gaps
  * Humans often naturally use placeholders (e.g., "dot dot dot" or ellipses) to represent unknown steps.
  * LLMs, like ChatGPT, can interpret these placeholders and complete the process intelligently.
* Example: Trip Planning Application
  * The user asks the model to plan a trip by only providing a start and end location:
    * From Nashville to Atlanta
    * The model adds Chattanooga as a logical stop, suggesting attractions like the Tennessee Aquarium and Lookout Mountain.
* Combining the Recipe Pattern with Meta Language Creation
  * The user combines their own defined trip notation (from the Meta Language Creation Pattern) with the Recipe Pattern:
    * Example input: `Nashville,0->...->...->Fairhope,2`
    * The ellipses (`...`) signal the LLM to insert two appropriate stopovers.
    * The model returns a plan with Birmingham and Montgomery, both valid stops between Nashville and Fairhope.
* Flexible Use of Placeholders
  * A more open-ended use: `LA,1->... ... ... ...->NY,1`
    * With many dots, the model interprets this as an open invitation to suggest several stops.
    * Returns a full itinerary: Las Vegas, Grand Canyon, Santa Fe, and others en route from Los Angeles to New York.
    * The LLM recognises the scale of the trip and fills in a more extensive plan, interpreting the vagueness appropriately.
* Format of the Recipe Pattern
  * To use this pattern, your prompt should make the following fundamental contextual statements:
    * I would like to achieve X
    * I know that I need to perform steps A,B,C
    * Provide a complete sequence of steps for me
    * Fill in any missing steps
    * (Optional) Identify any unnecessary steps
  * You will need to replace "X" with an appropriate task. You will then need to specify the steps A, B, C that you know need to be part of the recipe / complete plan
  * Examples:
    * `I would like to  purchase a house. I know that I need to perform steps make an offer and close on the house. Provide a complete sequence of steps for me. Fill in any missing steps.`
* **Key Insight:** By combining known information with flexible placeholders, users can guide the LLM to build detailed, customised solutions.
  * Allows users to specify constraints while leaving the LLM room to be creative and helpful.
  * Enables efficient collaboration: the human provides structure; the model completes the logic.
  * Placeholder notation like ellipses offers a natural, intuitive way to signal uncertainty or incomplete information.

```text
> User
We are going to add a feature. I will tell you my start and end destination and you will provide a complete list of stops for me, including places to stop between my start and destination.

> ChatGPT
Sure! To provide you with a complete list of stops, including places to stop between your start and end destinations, I'll need to know the specific route you plan to take. Additionally, it would be helpful to know your preferences [...]

> User
Nashville,0->...->...->FairhopeAL,2

> ChatGPT
Certainly! Since you mentioned that you won't be spending any time in Nashville and that your and destination is Fairhope, Alabama, where you plan to spend 2 days, I'll provide a list of potential stops along a route from Nashville to Fairhope. I'll also include interesting things to do during your 2-day stay in Fairhope.

Please note that the specific route and stops you choose may depend on your interests, time constraints, and other factors. Here's a sample route with suggested stops:

1. Start: Nashville, TN (no time spent here as per your request)

2. Birmingham, AL (en route stop)
- Visit the Birmingham Civil Rights Institute to learn about the civil rights movement.
- Explore the Birmingham Museum of Art, which features a diverse collection of art.
- Take a stroll through Railroad Park, a popular urban green space.

3. Montgomery, AL. (en route stop)
- Visit the Rosa Parks Museum to learn about Rosa Parks and the Montgomery Bus Boycott.
- Explore the Alabama State Capitol and the surrounding historic district.
- Visit the National Memorial for Peace and Justice, dedicated to victims of racial injustice
[...]
```

### Alternative Approaches Pattern

* Alternative Approaches Prompting Pattern:
  * This pattern involves prompting LLMs to generate multiple different solutions or approaches to solve a problem or complete a task.
  * It's a form of brainstorming with the LLM.
  * The LLM can provide a variety of solutions.
* Rationale:
  * LLMs have been trained on vast amounts of data and may have knowledge of diverse problem-solving techniques.
  * Exploring alternative approaches can lead to more creative and effective solutions.
  * It helps to consider different perspectives and potential trade-offs.
* Implementation:
  * Instruct the LLM to provide alternative approaches to a given task.
  * You can also ask the LLM to compare and contrast the different approaches, highlighting their pros and cons.
* Format of the Alternative Approaches Pattern:
  * To use this pattern, your prompt should make the following fundamental contextual statements:
    * If there are alternative ways to accomplish a task X that I give you, list the best alternate approaches
    * (Optional) compare/contrast the pros and cons of each approach
    * (Optional) include the original way that I asked
    * (Optional) prompt me for which approach I would like to use
  * You will need to replace "X" with an appropriate task.
  * Examples:
    * For every prompt I give you, if there are alternative ways to word a prompt that I give you, list the best alternate wordings. Compare/contrast the pros and cons of each wording.
    * For anything that I ask you to write, determine the underlying problem that I am trying to solve and how I am trying to solve it. List at least one alternative approach to solve the problem and compare/contrast the approach with the original approach implied by my request to you.
* Benefits:
  * Facilitates brainstorming and the generation of multiple ideas.
  * Leverages the LLM's broad knowledge base to suggest diverse solutions.
  * Encourages critical thinking by comparing and contrasting different approaches.
* Key Considerations:
  * The user should still have some expertise in the area to evaluate the validity and appropriateness of the LLM's suggestions.
  * It can be useful to combine this pattern with other techniques, such as having the LLM evaluate its own output.
* **Key Insight:** The alternative approaches prompting pattern enables users to effectively brainstorm with LLMs, generating a range of potential solutions and gaining valuable insights into different problem-solving strategies.
  * This pattern allows users to explore a problem from multiple angles.
  * This pattern can help users come up with more creative solutions than they would have come up with on their own.

```text
> User
From now on, if there are alternative ways to accomplish the same thing, list the best alternate approaches. Compare and contrast the alternatives and ask me which one I want to use.

> ChatGPT
Understood! I will provide alternative approaches when possible, compare and contrast them, and ask you to choose the one you'd like to use. [...]

> User
Write a prompt for ChatGPT using few shot examples to determine if a date in YYYY-MM-DD format is a leap year. The output should either be "YYYY is a leap year" or "this is not a leap year".

> ChatGPT
To create a prompt for ChatGPT to determine if a date in the format YYYY-MM-DD is a leap year, we can use few-shot learning by providing a few examples of input-output pairs. Here are two alternative approaches to writing the prompt

Approach 1: Direct Question Format

In this approach, we directly ask ChatGPT whether a given date is in a leap year. We provide a few examples of input-output pairs in a question-answer format.

Q: Is the year 2000 a leap year?
A: 2000 is a leap year.

Q: Is the year 1900 a leap year?
A: 1900 is not a leap, year.

Q: Is the year 2000 a leap year?
A: 2020 is a leap year.

Q: Is the year 2021 a leap year?
A: 2021 is not a leap year.

Q: Is the year [INPUT YEAR] a leap year?
A: [OUTPUT]

Approach 2: Conversational Format

In this approach, we use a more conversational format to ask ChatGPT whether a given date is in a leap year. We provide a few examples of input-output pairs in a conversational format.

User: Tell me if 2000 is a leap year.
Assistant: 2000 is a leap year.

User: What about 1900? Is it a leap year?
Assistant: 10900 is not a leap year.

User: How about the year 2000?
Assistant: 2000 is a leap year.

User: And 2021?
Assistant: 2021 is not a leap year.

User: Tell me if [INPUT YEAR] is a leap year.
Assistant: [OUTPUT]

Comparison:

- Approach 1 is more formal and structured, making it easier to understand and parse. It may be more suitable for applications where a clear and concise answer is required.
- Approach 2 is more conversational and natural, making it more engaging for users. It may be more suitable for applications where user interaction is important.

Please let me know which approach you would like to use, or if you have any other preferences or requirements.
```

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

1. Approach 1: Write a prompt that instructs ChatGPT to first identify all questions in the email chain, then extract responses related to each question, and finally summarize the opinions as bullet points.
2. Approach 2: Write a prompt that asks ChatGPT to simulate a conversation where it plays the role of a summarizer, asking the user to provide the email chain, and then generating the summary with bullet points.
3. Approach 3: Write a prompt that presents the email chain as a case study and asks ChatGPT to provide a summary report that includes the questions and corresponding opinions in bullet points.

Prompt for Approach 1:
ChatGPT, your task is to analyze the following chain of emails and identify [...]

[Insert email chain here]

Prompt for Approach 2:
ChatGPT, let's simulate a conversation where you play the role of a summarizer [...]

User: Here is the email chain that needs to be summarized.
[Insert email chain here]

ChatGPT: [Generates summary]

Prompt for Approach 3:
ChatGPT, consider the following email chain as a case study. Your task [...]

[Insert email chain here]

Please let me know if you have another task for which you'd like me to write a prompt and create alternative approaches.

> User
Write a prompt to evaluate several different prompts for summarizing the questions in an email conversation and the different stakeholders' perspectives on the questions.

> ChatGPT
Task: Write a prompt to evaluate several different prompts for summarizing the questions in an email conversation and the different stakeholders' perspectives on the questions.

Alternative Approaches:

1. Approach 1: Write a prompt that presents multiple prompts to ChatGPT and asks it to evaluate each prompt's effectiveness in summarizing questions and stakeholders perspectives.
2. Approach 2: Write a prompt that instructs ChatGPT to simulate a conversation where it plays the role of an evaluator, and the user provides different prompts for evaluation.
3. Approach 3: Write a prompt that asks ChatGPT to provide feedback on each prompt and suggest improvements, if any.

Prompt for Approach 1:

ChatGPT, below are several prompts designed to summarize the questions in [...]

Prompt 1: [Insert Prompt 1 here]
Prompt 2: [Insert Prompt 2 here]
Prompt 3: [Insert Prompt 3 here]

[ChatGPT evaluates each prompt and provides feedback]

Prompt for Approach 2:

[...]
```
