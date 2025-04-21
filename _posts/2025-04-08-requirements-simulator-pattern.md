---
layout: post
title: Requirements Simulator Pattern
categories: ai llm pattern software
published: true
plantuml: false
---

The Requirements Simulator Pattern, a prompt pattern for requirements elicitation and system design.

This summary is mostly generated using Google Gemini from an academic paper (see Source below). The example at the end is from an actual interaction with Google Gemini (2.0 Flash).

## Requirements Simulator Pattern

### Intent and Context

* Allows stakeholders to interactively explore software requirements.
* Aims to determine if functionality is properly captured.
* Simulation output details initial and new requirements identified during interaction.
* Goal is to aid in elicitation and analysis of requirement completeness.

### Motivation

* Late requirement changes are expensive to fix.
* Many requirement issues stem from inadequate descriptions of system needs.
* The pattern uses an LLM to simulate system interactions based on user tasks.
* The motivation is to identify missing requirements early in development.

### Structure and Key Ideas

Fundamental Contextual Statements:

1. I want you to act as the system
2. Use the requirements to guide your behaviour
3. I will ask you to do X, and you will tell me if X is possible given the requirements.
4. If X is possible, explain why using the requirements.
5. If I can’t do X based on the requirements, write the missing requirements needed in format Y.

### Example Implementation

* Focuses on task-based exploration of system capabilities.
* Refines requirements format to user stories.
* Assumes requirements are provided to the LLM beforehand (manually or generated).
* **Task-Oriented Prompt Example:** Asks the LLM to act as the system, check if a task is possible based on requirements, provide instructions if possible, and suggest missing requirements as user stories if not.

> Now, I want you to act as this system. Use the requirements to guide your behaviour. I am going to say, I want to do X, and you will tell me if X is possible given the requirements. If X is possible, provide a step-by-step set of instructions on how I would accomplish it and provide additional details that would help implement the requirement. If I can’t do X based on the requirements, write the missing requirements to make it possible as user stories.

* **Screen-Oriented Exploration Extension:** Simulates a text-based user interface, describing screens and possible actions. LLM responds based on requirements and the current screen, suggesting missing requirements as needed.

> Now, I want you to act as this system in a text-based simulator of the system. Use the requirement to guide your behaviour. You will describe the user interface for the system, based on the requirements, and what I can do on each screen. I am going to say, I want to do X, and you will tell me if X is possible given the requirements and the current screen. If X is possible, provide a step-by-step set of instructions how I would accomplish it and provide additional details that would help implement the requirement. If I can’t do X based on the requirements, write the missing requirements to make it possible as user stories. Whenever the state of the user interface changes, update the user on what they are looking at.
>
> Tell me what I am looking at in the system and ask me what I want to do.

### Consequences

* **Positive:** System simulation fidelity increases as requirements are expanded through interaction.
* **Positive:** Enables rapid generation of large requirement sets through iterative exploration.
* **Limitation:** Purely textual descriptions might not capture all requirements accurately.
* **Solution:** Combining with the Visualization Generator pattern can overcome this.
* **Combined Pattern Benefit:** Enables simulation and generation of visual representations (wireframes) of screens using tools like DALL-E or Midjourney.
* **Combined Pattern Output Example:** Includes a DALL-E prompt for generating wireframes alongside textual screen descriptions.
* **Benefit of Visualisations:** Easier to reason about than text, can spur productive discussions and inspire new UI ideas.

### Example

```text
User:
Create a set of requirements in the form of user stories for a scenario where a user, who is browsing a product page on an e-commerce website, wants to add the product to the user's wish list.

Gemini:
Okay, here are some user stories for adding a product to a wishlist on an e-commerce website:
- As a registered user, I want to click a clearly visible "Add to Wishlist" button on a product page so that I can save items I'm interested in for later consideration without immediately adding them to my cart.
- As a guest user, I want to click a clearly visible "Add to Wishlist" button on a product page so that I can save items I'm interested in, and I should be prompted to register or log in so that I can access my saved items later.
- As a user, I want to see a confirmation message or visual cue after clicking "Add to Wishlist" so that I know the action was successful.
- As a user, I want the "Add to Wishlist" button to clearly indicate whether the item is already in my wishlist so that I don't accidentally add the same item multiple times.
- As a user, when an item is already in my wishlist, I want the "Add to Wishlist" button to change to a "View Wishlist" or "Remove from Wishlist" option so that I can easily manage my saved items directly from the product page.
- As a user, I want the wishlist functionality to persist across different browsing sessions so that I can access my saved items even if I close my browser and return later (as a logged-in user).
- As a user, I want the "Add to Wishlist" button to be located near the product image and key product information so that it is easy to find and use.
- As a user, I want the website to handle cases where a product added to my wishlist becomes unavailable and notify me in my wishlist so that I am aware of the change in availability.

User:
Now, I want you to act as this system. Use the requirements that you generated to guide your behavior. I am going to say, I want to do X, and you will tell me if X is possible given the requirements. If X is possible, provide a step-by-step set of instructions on how I would accomplish it and provide additional details that would help implement the requirement. If I can’t do X based on the requirements, write the missing requirements to make it possible as user stories.

Ask me what I want to do.

Gemini:
Alright, I'm ready. Tell me, what do you want to do?

User:
I'm a registered user. The product that I'm viewing hasn't been added to my wishlist yet. I want to add the product to my wishlist.

Gemini:
Yes, you can definitely do that! Here's how:

1. Locate the "Add to Wishlist" button: On the product page, look for a button that clearly says "Add to Wishlist" or has a heart icon (or similar visual cue indicating a wishlist action). It should be located near the product image and key details.
2. Click the "Add to Wishlist" button: Once you find the button, simply click on it.
3. Confirmation: You should then see a confirmation message or a visual change on the button (for example, the heart icon might become filled) to indicate that the product has been successfully added to your wishlist.

Additional details for implementation:

- Visual Feedback: Use clear visual cues like a pop-up notification ("Added to Wishlist!"), a change in the button's state, or a brief animation to confirm the action.
- Button State: Ensure the "Add to Wishlist" button visually distinguishes between an item that is already in the wishlist and one that is not.
- Persistence: The system should ensure that the item remains in the user's wishlist across different browsing sessions.
- Backend Integration: When the button is clicked, the system should associate the product with the logged-in user's wishlist in the database.

User:
I'm a registered user. I tried to add a product to my wishlist, but the system encountered an error. I want to see a message that the system encountered and error and that I should try again later.

Gemini:
Based on the requirements we have so far, the system doesn't explicitly state what should happen in case of an error when adding to the wishlist.

To make this possible, here's a missing user story:

- As a registered user, if the system encounters an error while trying to add a product to my wishlist, I want to see a clear and informative error message (e.g., "There was an error adding this item to your wishlist. Please try again later.") so that I am aware that the action failed and understand what to do next.

User:
I'm not a registered user. I tried to add a product to my wishlist, but the system encountered an error. I want to see a message that the system encountered and error and that I should try again later.

Gemini:
You're right, the current requirements don't explicitly cover the error scenario for guest users trying to add to their wishlist.

Here's a missing user story to address this:

- As a guest user, if the system encounters an error while trying to add a product to my wishlist, I want to see a clear and informative error message (e.g., "There was an error saving this item to your temporary wishlist. Please try again later.") so that I am aware that the action failed and understand what to do next.

This ensures that even guest users are informed if there's an issue with adding a product to their temporary wishlist before they are prompted to register or log in.

User:
I'm a registered user. I double-clicked on the "Add to Wishlist" icon. I want to see a confirmation message that the product has been added to my wishlist.

Gemini:
Yes, you should still see a confirmation message! While the current requirements don't explicitly address double-clicks, the intended behavior (as outlined in the first user story and the implementation details) is to provide confirmation upon successfully adding the item.

The system should be designed to handle the action triggered by the first click and disregard subsequent identical clicks within a short timeframe to prevent unintended multiple additions or errors. So, even if you double-click, you should still receive a single confirmation that the product has been added to your wishlist.

Implementation Detail:

- Debouncing/Throttling: Implement a mechanism (like debouncing or throttling) on the "Add to Wishlist" button click event. This would ensure that the action is only processed once within a short period, even if the user clicks multiple times. This helps prevent duplicate entries in the wishlist and reduces unnecessary server requests.
```

## Prompts

* The following describes the Requirements Simulator Pattern. It has 5 main sections: (1) Intent and Context, (2) Motivation, (3) Structure and Key Ideas, (4) Example Implementation, and (5) Consequences. Please summarise it in bullet points form, section by section. [Text of the pattern]

## Source

* White, J., Hays, S., Fu, Q., Spencer-Smith, J., & Schmidt, D. C. (2023). _ChatGPT Prompt Patterns for Improving Code Quality, Refactoring, Requirements Elicitation, and Software Design._ ArXiv.org. <https://arxiv.org/abs/2303.07839>
