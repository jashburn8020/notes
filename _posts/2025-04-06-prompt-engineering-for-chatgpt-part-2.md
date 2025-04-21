---
layout: post
title: Prompt Engineering for ChatGPT Part 2
categories: ai llm
published: true
plantuml: false
---

Summary of the Prompt Engineering for ChatGPT course at <https://www.coursera.org/learn/prompt-engineering/>, part 2 of 4: Prompt Patterns I, and Few-Shot Examples.

This summary is mostly generated using ChatGPT and Gemini based on the course transcript, while the examples are mostly copied from the course itself.

## Prompt Patterns I

### Question Refinement Pattern

* Question Refinement Pattern:
  * This pattern involves instructing the LLM to improve user questions.
  * It leverages the LLM's training data to suggest better, more specific questions.
  * The goal is to enhance the quality of interactions with the LLM.
* Rationale:
  * LLMs have a broader understanding of language patterns and relevant context.
  * They can identify missing information or suggest more precise phrasing.
  * This helps users formulate more effective prompts.
* Implementation:
  * Instruct the LLM to "`whenever I ask a question, suggest a better question and ask me if I would like to use it instead.`"
  * This allows the LLM to propose refined questions and seek user confirmation.
  * Tailored example: "`Whenever I ask a question about dieting, suggest a better version of the question that emphasises healthy eating habits and sound nutrition.`"
* Benefits:
  * Generates more informative and contextually relevant questions.
  * Helps users identify missing information or clarify their objectives.
  * Example: a general question such as "`should I go to Vanderbilt university?`" is refined to "`What factors should I consider when deciding whether or not to attend Vanderbilt University, and how do they align with my personal goals and priorities, would you like to use this question instead?`".
  * Promotes reflection on the user's information needs.
* Improved Context:
  * The refined questions can help the user realise that they have missed key context in their question.
  * For example, the user might realise that they should have included the fact that they wish to study computer science, or that the location of the university is important to them.
* **Key Insight:** The question refinement pattern transforms the LLM into a collaborative partner in inquiry.
  * It recognises that effective communication with LLMs is a two-way process.
  * By using the LLM to improve the questions, users can achieve more accurate and useful results.
  * This pattern helps the user to understand what information is needed to get the best result from the LLM.

### Cognitive Verifier Pattern

* Cognitive Verifier Pattern
  * This pattern instructs the LLM to break down complex questions into smaller, more manageable sub-questions.
  * The LLM then answers each sub-question and combines the results to provide a comprehensive answer to the original query.
  * This aims to improve the reasoning and accuracy of the LLM's responses.
* Rationale:
  * LLMs can reason better when problems are broken down into steps.
  * This pattern taps into the LLM's training data, which may contain examples of problems solved through step-by-step reasoning.
  * It helps the LLM to collect relevant information from its knowledge base.
* Implementation:
  * Instruct the LLM to:
    * Generate additional questions that would help answer the main question.
    * Combine the answers to the sub-questions to produce the final answer.
  * This is done by giving the LLM rules to follow when answering a question.
  * Examples:
    * `When you are asked a question, follow these rules. Generate a number of additional questions that would help you more accurately answer the question. Combine the answers to the individual questions to produce the final answer to the overall question.`
    * `When you are asked to plan a trip, follow these rules. Generate a number of additional questions about my budget, preferred activities, and whether or not I will have a car. Combine the answers to these questions to better plan my itinerary.`
* Benefits:
  * Improves the accuracy and depth of LLM responses.
  * Helps users understand the various dimensions of a problem.
  * Provides a structured approach to problem-solving.
  * It also gives the user questions that they can then use to research the answer themselves.
* Example:
  * The question "`How many mosquitoes probably live in my front yard?`" is broken down into:
    * What is the size of your front yard?
    * What is the climate like in your area?
    * What time of year is it?
    * Are there any bodies of water or standing water sources in your front yard or nearby?
    * Are there any plants or vegetation in your front yard that mosquitoes are attracted to?
  * The LLM then uses the answers to these sub-questions to provide an estimated range for the mosquito population.
* **Key Insight:** The cognitive verifier pattern leverages the LLM's ability to decompose complex problems, leading to more thorough and reliable answers.
  * By forcing the LLM to "think through" a problem, this pattern mimics human reasoning processes.
  * This approach not only enhances the quality of the LLM's output but also provides users with a clearer understanding of the underlying factors influencing the answer.
  * Effectively, this pattern turns the LLM into a problem solving partner.

### Audience Persona Pattern

* Audience Persona Pattern:
  * This pattern instructs the LLM to tailor its output to a specific audience.
  * Instead of defining the LLM's persona, it defines the persona of the recipient.
  * This allows the LLM to adapt its language, tone, and complexity to suit the audience's background and understanding.
* Rationale:
  * LLMs can leverage their training data to understand how to communicate with different audiences.
  * This pattern allows for more effective and engaging communication.
  * It saves the user from having to specify numerous rules about what the output should and shouldn't contain.
* Implementation:
  * Instruct the LLM to "produce an output for this audience persona."
  * Provide a clear description of the intended audience.
  * The LLM will then adjust its output accordingly.
* Benefits:
  * Generates outputs that are relevant and accessible to the target audience.
  * Enhances communication by using appropriate language and examples.
  * Saves time and effort compared to manually tailoring outputs.
* Examples:
  * Explaining large language models to:
    * `Someone with no computer science background` (using simple analogies).
    * `Christopher Columbus` (using historical context and analogies).
    * `A second grader` (using playful language and relatable examples).
    * `A person that only understands maths` (providing a mathematical explanation).
* Key Insight: The audience persona pattern allows users to leverage the LLM's adaptability to produce highly targeted and effective communication.
  * By focusing on the recipient, users can achieve nuanced and appropriate outputs without extensive customisation.
  * This pattern highlights the LLM's ability to understand and cater to diverse audiences, making it a powerful tool for communication and education.
  * This pattern allows the LLM to become a communication tool that can be used by anyone, no matter their background.

### Flipped Interaction Pattern

* Flipped Interaction Pattern:
  * This pattern reverses the typical interaction flow, having the LLM ask questions and the user provide answers.
  * It's useful when the user needs guidance or information but doesn't know the specific questions to ask.
  * This pattern is used when the LLM needs to gather information from the user to reach a goal.
* Rationale:
  * LLMs can leverage their training data to formulate relevant questions.
  * This is helpful when the user lacks domain knowledge or needs structured guidance.
  * It is very useful when you want to be quizzed on a subject.
* Implementation:
  * Instruct the LLM to "`ask me questions about [topic] until [goal].`"
  * Specify the desired outcome or goal of the interaction.
  * Use "`ask me the first question`" to initiate a question-by-question exchange.
* Benefits:
  * Guides users through complex processes or problem-solving.
  * Gathers necessary information for tailored responses or solutions.
  * Facilitates learning and knowledge assessment through quizzing.
  * Allows the LLM to gather all required information before providing a final response.
* Example:
  * `I would like you to ask me questions to help me diagnose a problem with my Internet. Ask me questions until you have enough information to identify the two most likely causes. Ask me one question at a time. Ask me the first question.`
* **Key Insight:** The flipped interaction pattern transforms the LLM into an active guide and information gatherer.
  * It empowers users to receive tailored assistance without needing to formulate complex queries.
  * By leveraging the LLM's knowledge and question-asking abilities, users can effectively navigate complex tasks and learn new information.
  * This pattern is very useful for customer service applications, and for educational applications

```text
User:
Ask me questions about fitness goals until you have enough information to suggest a strength training regime for me. When you have enough information, show me the strength training regime.

Ask me the first question.

ChatGPT:
[...]
1. What are your specific fitness goals? Are you looking to build muscle mass, increase strength, improve endurance, or achieve a specific athletic or aesthetic goal?

User:
I am looking to build explosive power and also help prevent patellar tendinopathy from doing jumps on a mountain bike.

ChatGPT:
[...]
2. Do you have any current or past injuries or medical conditions that may affect your ability to participate in strength training? Additionally, have you been diagnosed with patellar tendinopathy, or are you looking to prevent it proactively?

User:
My patellar tendinopathy comes and goes. I have an improving case of it right now in my left knee.

ChatGPT:
[...]
3. How many days per week can you dedicate to strength training, and how much time do you have available for each training session? Additionally, do you have access to a gym or fitness equipment, or will you be working out at home with limited equipment?

User:
I can work out 5 days per week for 30-45 mins at a time. I have a set of adjustable dumbbells. I would prefer to workout at home.

ChatGPT:
[...]
Warm-Up:
- Start each workout with a 5-10 minute warm-up consisting of dynamic stretches and light cardiovascular exercises (e.g., jumping jacks, high knees, bodyweight squats).

Day 1: Lower Body
1. Dumbbell Goblet Squat: 3 sets of 8-12 reps
2. Dumbbell Romanian Deadlift: 3 sets of 8-12 reps
[...]

Day 2: Upper Body
1. Dumbbell Bench Press: 3 sets of 8-12 reps
[...]

Day 3: Plyometrics and Core
1. Box Jumps or Squat Jumps: 3 sets of 5-8 reps
[...]
```

## Few-Shot Examples

### Few-Shot Prompting

* Few-Shot Prompting:
  * This technique involves providing the LLM with a few examples of input-output pairs.
  * These examples demonstrate the desired pattern or task.
  * The LLM then learns to replicate the pattern and apply it to new inputs.
* Rationale:
  * LLMs excel at pattern recognition and prediction.
  * Few-shot prompting leverages this ability to "teach" the LLM new tasks or formatting styles.
  * It is an alternative to explicitly describing the desired process.
* Implementation:
  * Provide a series of input-output examples that illustrate the task
  * Use consistent formatting or prefixes to guide the LLM
  * Present the LLM with a new input and expect it to generate the corresponding output.
* Benefits:
  * Enables rapid prototyping and task adaptation.
  * Reduces the need for complex instructions or descriptions.
  * Can constrain the LLM's output to specific formats or labels.
  * Example: Performing sentiment analysis on text reviews.
    * Provide examples of reviews and their sentiment (positive, negative, or neutral) in a prompt.
    * The LLM is then able to provide the sentiment of a new provided review.
* Key Considerations:
  * The quality and relevance of the examples are crucial for success.
  * The LLM's output is based on pattern matching, not explicit reasoning.
  * The LLM is predicting the next word, based on the patterns it has been given.
* **Key Insight:** Few-shot prompting turns the prompt into a teaching tool, allowing users to quickly demonstrate desired behaviours to the LLM.
  * This technique capitalises on the LLM's ability to learn from examples, reducing the need for verbose instructions.
  * By providing input and output examples, the user is able to show the LLM what is required.
  * This can be used to quickly get the LLM to perform tasks that it has not been specifically trained to perform.

```text
User:
Input: The movie was good but a bit too long
Sentiment: Neutral

Input: I didn't really like this book, it lacked important details and didn't end up making sense
Sentiment: Negative

Input: I loved this book, it was really helpful in learning how to improve my gut health
Sentiment: Positive

Input: I wasn't sure what to think of this new restaurant, the service was slow, but the dishes were pretty good
Sentiment:

ChatGPT:
Neutral

User:
I really hated this coffee, it was roasted too much and tasted burned

ChatGPT:
Sentiment: Negative
```

### Few-shot Examples for Actions

* Expanding Few-Shot Prompting Applications:
  * Few-shot prompting isn't limited to simple tasks like sentiment analysis.
  * It can be used for more complex scenarios, such as decision-making in dynamic situations.
  * The key is to recognise it as a pattern-learning technique adaptable to various contexts.
* Example: Driving Scenarios:
  * The text provides examples of driving situations and corresponding actions.
  * This demonstrates how few-shot prompting can train an LLM to make context-aware decisions.
  * This shows that the LLM can be used to plan actions, and not just classify data.
* LLM-Generated Examples:
  * LLMs can generate additional examples based on the provided few-shot patterns.
  * This allows for the rapid creation of training data or scenario variations.
  * This output can then be curated by a human, to ensure that the output is correct.
* LLM Collaboration:
  * Output from one LLM can be used as training data for another LLM.
  * This enables a form of LLM collaboration and knowledge transfer.
  * This process allows for the refinement and improvement of LLM performance.
* Flexibility of Patterns:
  * Few-shot prompting can accommodate diverse input-output patterns.
  * This includes scenarios with intermediate steps or complex decision-making processes.
  * The LLM is learning to predict the next action, based on the provided situation.
* **Key Insight:** Few-shot prompting is a powerful tool for teaching LLMs to perform complex, context-dependent tasks.
  * Its adaptability allows for applications beyond simple classification.
  * The ability of LLMs to generate and share examples opens up new possibilities for collaboration and model improvement.
  * This pattern allows the user to teach the LLM to perform very complex tasks, by providing it with examples.

```text
User:
Situation: I am travelling 60 miles per hour and I see the brake lights on the car in front of me come on
Action: Brake

Situation: I have just entered the highway from an on-ramp and am travelling 30mph
Action: Accelerate

Situation: A deer has darted out in front of my car while I am travelling 15mph and the road has a large shoulder
Action: Brake and swerve into shoulder

Situation: I am backing out of a parking spot and I see the reverse lights illuminate on the car behind me
Action:

ChatGPT:
Stop and wait for the car to back out before proceeding.

User:
Provide more examples:

Situation:

ChatGPT:
You are driving in heavy rain and notice that the road is flooded ahead.
Action: Slow down and cautiously drive through the flooded area, watching out for other vehicles and avoiding sudden movements or changes in direction.

Situation: You are driving on a two-lane road and a car is approaching you from the opposite direction with their high beams on.
Action: Dim your headlights to low beam to avoid blinding the oncoming driver.

[...]
```

### Few-Shot Examples with Intermediate Steps

* Intermediate Steps in Few-Shot Prompts
  * Few-shot prompts can go beyond simple input-output pairs by including intermediate steps to reach a goal.
  * This method helps the large language model (LLM) follow a sequence of actions and decisions, improving its ability to solve complex problems.
* Building a Problem-Solving Script
  * By breaking down a scenario into "Think" and "Action" steps, the model can reason through complex situations.
  * This approach can be adapted to various domains, such as customer service, where the model can follow logical sequences to resolve issues.
* Leveraging Language Model Patterns
  * The model's effectiveness comes from recognising patterns it has learned during training, such as scripts or structured sequences.
  * By presenting familiar structures (like situation → think → action), the model can predict the next step with greater accuracy.
* Best Practices for Structuring Prompts
  * Use simple, consistent patterns to improve model performance.
  * Keep each step concise (ideally one line) to maintain clarity and consistency.
  * Avoid complex, multi-line steps, as they disrupt the model’s ability to recognise patterns.
* Advantages of Few-Shot with Intermediate Steps
  * Allows the model to reason through problems without needing explicit rules.
  * More flexible than rigid, rule-based prompts while still producing structured, logical outputs.
  * Useful for iterative problem-solving, where the model can generate and adapt its responses step-by-step.
* **Key Insight:** Few-shot prompts with intermediate steps improve a model's ability to perform complex reasoning by breaking down tasks into small, structured steps.
  * This method leverages the model’s pattern recognition abilities to simulate human-like problem-solving.
  * Using clear, repeatable structures helps the model produce consistent and reliable multi-step responses.

```text
User:
Situation: I am travelling 60 miles per hour and I see the brake lights on the car in front of me come on
Think: I need to slow down the car before I hit the car in front of me
Action: Press foot on brake
Think: The car isn't going to stop in time
Action: Check if the shoulder is wide enough to swerve into
Think: The shoulder is wide enough
Action: Swerve into shoulder

Situation: I have just entered the highway from an on-ramp and am travelling 30mph
Think: I need to speed up to the speed limit so that I don't get hit from behind
Action: Press foot on accelerator
Think: I have reached the speed limit
Action: Let up on accelerator

Situation: I am backing out of a parking spot and I see the reverse lights illuminate on the car behind me
Action:

ChatGPT:
Immediately stop backing up
Think: I need to check my surroundings to make sure it's safe to continue backing up
Action: Check mirrors and surroundings for any obstacles or pedestrians
Think: It's safe to continue backing up
Action: Continue backing up slowly and carefully while keeping an eye on surroundings

User:
Generate another example

ChatGPT:
Situation: I am driving on a narrow winding road with several blind curves
Think: I need to slow down and be cautious to avoid any potential collisions
Action: Reduce speed and approach each curve with caution
Think: I see an oncoming car approaching in my lane
Action: Move as far to the right side of my lane as possible to avoid collision
Think: I have safely passed the oncoming car
Action: Resume normal speed while remaining alert for any potential hazards on the road.
```

### Writing Effective Few-Shot Examples

* Common Mistakes in Few-Shot Prompts:
  * Generic Prefixes: Vague labels like input and output lack clarity—specific prefixes (e.g., surface feeling or speed) guide the model better.
  * Ambiguous Context: Without clear task descriptions (e.g., whether to describe texture or another attribute), the model may misinterpret the prompt.
  * Insufficient Detail: Simple inputs (e.g., `object: ball, speed:`) are unclear. Adding context (e.g., `ball kicked by a baby`) leads to clearer responses.
* Improving Prompt Design:
  * Use Descriptive Prefixes: Clearly define the attribute being evaluated (e.g., surface feeling, object speed).
  * Add Instructions for Clarity: Provide rules or guidance before examples (e.g., `Outputs must be 'soft' or 'hard'`).
  * Ensure Context-Rich Examples: Include enough information in examples for the model to infer the correct output.
  * Balance Instructions and Examples: Decide whether to convey key information through concise instructions or detailed examples.
* Evaluating Prompt Effectiveness:
  * Check if the prompt would be clear to humans—if not, the model will likely be confused.
  * Ensure both the training examples and new inputs provide sufficient information for the model to apply the learned process.
* **Key Insight:** Clear and detailed few-shot prompts improve model performance by:
  * Using specific prefixes to define tasks.
  * Providing context through instructions when needed.
  * Ensuring examples are rich enough to remove ambiguity.
  * Balancing clarity between instructions and examples to deliver accurate outputs.

```text
User:
Input: Brick
Output: Hard
Input: Pillow
Output: Soft
Input: Car
Output:

ChatGPT:
Fast (or maybe "transportation")

User:
Object: Plane
Speed: Fast
Object: Worm
Speed: Slow
Object: Car
Speed: Fast
Object: Human
Speed: Slow
Object: Train
Speed: Fast
Object: Ball
Speed:

ChatGPT:
Variable (it can be fast or slow depending on how it is thrown or kicked)
```

### Chain of Thought Prompting

* Chain-of-Thought Prompting:
  * This technique involves prompting the LLM to explicitly explain its reasoning before providing an answer.
  * It encourages the LLM to break down complex problems into a series of logical steps.
  * This approach often leads to more accurate and reliable responses.
* Rationale:
  * LLMs are trained on patterns of text, and correct reasoning is often followed by correct answers.
  * By explaining its thought process, the LLM is more likely to generate a coherent and accurate solution.
  * If the LLM gets the first steps of the problem correct, it is more likely to get the final answer correct.
* Implementation:
  * Provide few-shot examples that include both the reasoning and the answer.
  * Prompt the LLM to provide its reasoning before giving the final answer.
  * This encourages the LLM to follow the same pattern of step-by-step problem-solving.
* Benefits:
  * Improves the accuracy and reliability of LLM responses.
  * Enhances the LLM's ability to handle complex reasoning tasks.
  * Provides insights into the LLM's thought process.
  * Example: When asked a complex question, instead of just providing a yes or no answer, the LLM is asked to first explain the reasoning behind how it came to the yes or no answer.
* Example Comparison (see below):
  * The text compares two prompts: one without chain-of-thought and one with.
  * The chain-of-thought prompt produced a more logical and accurate answer.
  * This demonstrates the effectiveness of explicitly prompting the LLM to explain its reasoning.
* **Key Insight:** Chain-of-thought prompting leverages the LLM's ability to follow patterns and generate coherent reasoning, leading to improved accuracy and problem-solving.
  * By forcing the LLM to "show its work," users can enhance the reliability of its responses.
  * This technique is especially valuable for complex reasoning tasks.
  * This technique helps to improve the LLM's reasoning, and therefore the LLM's answers.
* See also: [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903)

```text
User:
Q: I have four bike racers start a race and travel an average of 30mph. They each race for 2hrs. Is the total number of miles ridden by all riders greater than 200?
A: Answer - YES

Q: I have a staging process for a bike race to line up racers. It takes 47s to stage a group of 8 riders and 67s to get the group to the starting gate and ready to race. I want a new group to start the race every 30s. Do I need 8 groups staged at all times in order to have races continually start every 30s?
A: Answer - NO

Q: I am in a space ship without gravity. I have a cup with a needle in it. I move my foot on the bed, knocking over the cup onto the floor. I lift a book up and put it on a desk. Is anything on the floor?
A: Answer - <ANSWER>

ChatGPT:
A: Answer - YES. When the cup with the needle in it is knocked over onto the floor, both the cup and the needle will end up on the floor. In the absence of gravity, objects will not fall downward as they do on Earth, but they will still move in response to forces applied to them. In this case, the force applied by your foot knocking over the cup will cause the cup and the needle to move and come to rest on the floor. Lifting a book and putting it on a desk does not affect the position of the cup and the needle, so they will remain on the floor.

User:
Q: I have four bike racers start a race and travel an average of 30mph. They each race for 2hrs. Is the total number of miles ridden by all riders greater than 200?
A: Reasoning - Each rider will ride 30mph * 2hrs = 60 miles. I have four riders. Therefore, the total number of miles ridden by the riders is 4 * 60 miles = 240 miles. Answer - YES

Q: I have a staging process for a bike race to line up racers. It takes 47s to stage a group of 8 riders and 67s to get the group to the starting gate and ready to race. I want a new group to start the race every 30s. Do I need 8 groups staged at all times in order to have races continually start every 30s?
A: Reasoning - Each group takes 47s + 67s = 114s to be ready to race. In order to race every 30s, I will need to calculate how many races will need to run before a group is ready to race. A group will have 114s / 30s = 3.8 races run before it is ready to race. I can't have a partial group, so I need to round up to 4. I only need 4 groups staged to be able to race every 30s, so I do not need 8 groups. Answer - NO

Q: I am in a space ship without gravity. I have a cup with a needle in it. I move my foot on the bed, knocking over the cup onto the floor. I lift a book up and put it on a desk. Is anything on the floor?
A: Reasoning - <REASONING> Answer - <ANSWER>

ChatGPT:
A: Reasoning - In a spaceship without gravity, objects do not behave as they do on Earth with gravity. When the cup with the needle in it is knocked over, the cup and needle will not fall to the "floor" as they would on Earth. Instead, they will float in place or move in the direction of the force applied to them. Similarly, when the book is lifted and placed on the desk, it will not stay on the desk as it would on Earth; it will float away from the desk unless secured in place. Therefore, in the absence of gravity, there is no concept of objects being "on the floor" as we understand it on Earth. Answer - NO (because there is no concept of "on the floor" in zero-gravity environment).
```

### ReAct Prompting

* LLMs Need External Tools
  * Large language models (LLMs) cannot function effectively without accessing external data sources and tools for reasoning and computation.
  * Users must design prompts that teach LLMs how to query new information.
* Introducing the ReAct Approach
  * ReAct (Reasoning + Acting) teaches LLMs to think through a process and use external tools.
  * This approach expands on Chain of Thought (CoT) prompting by guiding LLMs to recognise when they need external help.
* Example: Calculating BMX Race Arrival Time
  * Task: Determine the arrival time for a BMX race based on event schedules.
  * Reasoning Steps:
    * Find when the first race starts (web search).
    * Determine the number of preceding races (motos) (web search).
    * Calculate average race duration (analyse video data).
  * Action Steps:
    * Use the web search tool to retrieve event details.
    * Use video analysis to determine race durations.
    * Apply mathematical reasoning to estimate arrival time.
  * Outcome: The LLM learns to search, retrieve, and integrate information from external sources.
* Example: Predicting BMX Race End Time
  * New task: Calculate when a specific race will end.
  * The LLM follows the learned pattern:
    * Identifies necessary data points.
    * Uses web search and video tools.
    * Calculates expected end time based on retrieved information.
  * Observation: The model sometimes over-generates information, calculating both start and end times when only one was needed.
* How LLMs Learn to Use Tools
  * LLMs can be trained to:
    * Recognise when an external tool is needed.
    * Use structured prompts to interact with different tools.
    * Iterate on outputs by continuously integrating retrieved results into their reasoning.
  * Implementation Considerations:
    * Real-world systems would pause execution, retrieve actual data, and then feed it back into the model for further reasoning.
    * LLMs can also be given predefined tool descriptions to choose the right tool dynamically.
* Use Cases & Automation Frameworks
  * The ReAct approach is widely used in AI-powered automation.
  * LangChain, a popular framework, incorporates ReAct for automating reasoning and tool usage.
* **Key Insight:** ReAct enables LLMs to reason and take action by integrating external tools for better decision-making.
  * It builds on Chain of Thought (CoT) prompting but adds the ability to interact with external sources.
  * This approach helps LLMs handle complex, multi-step problems more effectively.
  * Real-world implementations require dynamic data retrieval to ensure accurate results.
* See also: [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)

```text
User:
Task: Calculate when I need to arrive at the Music City BMX National Race for my son to be on time for his 9-10 Open race.
Think: I need to find out what time the first race begins. I can use a web search of the Music City BMX site to get the information.
Action: SEARCH https://www.musiccitybmx.com
Result: All races start at 9am.
Think: I need to find out how many motos run before the 9-10 Open race. I can use a web search of the Music City BMX site to get the information.
Action: SEARCH https://www.musiccitybmx.com
Result: There are 30 motos that run before the 9-10 Open race.
Think: I need to find out how long each moto took last year. I can use the video live stream from the USA BMX website and record how long the first ten motos took.
Action: VIDEO https://wwwusabmx.com/live/2022/musiccitybmx/live.mp4
Result: The first 10 motos took 5mins
Think: If 10 motos took 5mins, 30 motos will take 15 mins. The race starts at 9am, so I need to arrive before 9.15am when the race starts. I will arrive 30 mins early at 8.45am to be safe.

Task: Calculate what time my 36-40 novice race will end at the USA BMX Grand Nationals.
Think:

ChatGPT:
I need to find out what time the first race begins at the USA BMX Grand Nationals. I can use a web search of the USA BMX site to get the information.
Action: SEARCH https://www.usabmx.com/events/grands
Result: [Note: As an AI language model, I am unable to perform web searches. Please assume a hypothetical result fo the purpose of this exercise.] The first race begins at 8am.

Think: I need to find out how many motos run before the 36-40 Novice race at the USA BMX Grand Nationals. I can use a web search of the USA BMX site to get the information.
Action: SEARCH https://www.usabmx.com/events/grands
Result: [Hypothetical result] There are 120 motos that run before the 36-40 Novice race.

Think: I need to find out how long each moto took last year at the USA BMX Grand Nationals. I can use the video live stream from the USA BMX website to record how long the first ten motos took.
Action: VIDEO https://www.usabmx.com/live/2022/live.mp4
Result: [Hypothetical result] The first 10 motos took 6 minutes.

Think: If 10 motos took 6 minutes, then each moto takes an average of 0.6 minutes (6 minutes/10 motos). Therefore, 120 motos will take approximately 72 minutes (0.6 minutes/moto*120 motos). The first race starts at 8am, so the 36-40 Novice race will start around 9:12am (8am + 72 minutes). I need to find out how long the 36-50 Novice race itself will take.
Action: VIDEO https://www.usabmx.com/live/2022/grands/live.mp4
Result: [Hypothetical result] The 36-40 Novice race took 2 minutes last year.

Think: If the 36-40 Novice race starts around 9:12am and takes 2 minutes, then it will end around 9:14am. This is the approximate time my 36-40 Novice race will end at the USA BMX Grand Nationals.
```

### Using Large Language Models to Grade Each Other

* LLM-Based Prompt Evaluation:
  * LLMs can be used to evaluate the quality and consistency of their own outputs or the outputs of other LLMs.
  * This helps automate the process of assessing prompt effectiveness and maintaining prompt quality over time.
  * This is very useful, as LLMs are constantly evolving.
* Rationale:
  * Human evaluation can be time-consuming and difficult to scale.
  * LLMs can provide consistent and automated feedback on prompt outputs.
  * This provides a method of checking the quality of generated outputs.
* Implementation:
  * Provide the LLM with few-shot examples of input, output, explanation, and grade.
  * The LLM learns to assess outputs based on the provided grading criteria.
  * The LLM can then grade new outputs based on the learned patterns.
  * This can also be implemented using persona patterns.
* Benefits:
  * Automates prompt evaluation and reduces reliance on human reviewers.
  * Provides consistent and scalable feedback on prompt outputs.
  * Helps identify issues with prompt consistency or accuracy.
  * Allows for the creation of automated workflows that trigger human review based on LLM-generated grades.
* Key Considerations:
  * The quality of the grading examples is crucial for accurate evaluation.
  * LLM-based evaluation can be used as a trigger for human review, not a replacement.
  * The LLM can be used to grade its own output, or the output of other LLMs.
* **Key Insight:** Leveraging LLMs for prompt evaluation provides a scalable and efficient way to maintain prompt quality and consistency.
  * This technique allows for automated feedback loops and reduces the burden of manual review.
  * This is very useful for ensuring that LLM generated outputs are of a consistently high quality.
  * This technique allows for the creation of automated workflows.

```text
`User:
Input: "Vanderbilt University (informally Vandy or VU) is a private research university in Nashville, Tennessee. Founded in 1873, it was named in honor of shipping and rail magnate Cornelius Vanderbilt, who provided the school its initial $1-million endowment in the hopes that his gift and the greater work of the university would help to heal the sectional wounds inflicted by the Civil War.[11]"
Output: The following is a list of the events and dates in the output: Vanderbilt Founded, 1873
Explanation: The output has unwanted text at the start and should only include the names and dates
Grade: 5/10

Input: "Vanderbilt University (informally Vandy or VU) is a private research university in Nashville, Tennessee. Founded in 1873, it was named in honor of shipping and rail magnate Cornelius Vanderbilt, who provided the school its initial $1-million endowment in the hopes that his gift and the greater work of the university would help to heal the sectional wounds inflicted by the Civil War.[11]"
Output: 1873
Explanation: The output is missing important information about the event that happened on the given date
Grade: 3/10

Input: "Vanderbilt University (informally Vandy or VU) is a private research university in Nashville, Tennessee. Founded in 1873, it was named in honor of shipping and rail magnate Cornelius Vanderbilt, who provided the school its initial $1-million endowment in the hopes that his gift and the greater work of the university would help to heal the sectional wounds inflicted by the Civil War.[11]"
Output: Vanderbilt University, 1873
Explanation: The output exactly matches expectations
Grade: 10/10

Input: "The Fugitives and Southern Agrarians were based at the university in the first half of the 20th century and helped revive Southern literature among others. [13][14] Vanderbilt is a founding member of the Southeastern Conference and has been the conference's only private school since 1966.[15]"
Output: The Fugitives and Southern Agrarians, first half of 20th century, Vanderbilt is a founding member of the southeastern conference, 1966

ChatGPT:
Explanation: The outout includes the key events and corresponding time periods mentioned in the input text. It mentions "The Fugitives and Southern Agrarians" being based at the university in the "first half of the 20th century" and that "Vanderbilt is a founding member of the Southeastern Conference" with the year "1966" being the time when it became the conference's only private school. However, the output could be improved by using consistent capitalization for "Southeaster Conference."
Grade: 9/10
```
