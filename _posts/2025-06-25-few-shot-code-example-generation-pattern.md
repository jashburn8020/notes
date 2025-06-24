---
layout: post
title: Few-Shot Code Example Generation Pattern
categories: ai llm pattern software
published: true
plantuml: false
---

The Few-Shot Code Example Generation Pattern leverages an LLM to create concise code usage examples that can then be fed back to the LLM for efficient few-shot learning and to remind it of system designs.

This summary is mostly generated using Google Gemini from an academic paper (see Source below). The example at the end is from an actual interaction with Google Gemini (2.5 Flash), modified slightly for clarity and brevity.

## Few-Shot Code Example Generation Pattern

### Intent and Context

* Goal: Generate usage examples that can be provided to an LLM for **few-shot learning**.
* Few-shot Learning: Involves giving the LLM a limited set of training examples within a prompt.
* Code Examples:
  * Demonstrate proper code usage.
  * Can be more token-efficient than actual code for conveying function and use.
  * Help the LLM reason about the original code without seeing the full codebase.
  * Remind the LLM of prior design decisions.

### Motivation

* Problem: Large software systems or modules often exceed LLM token limits, making it difficult to describe design aspects or proper usage.
* Need: A way to remind the LLM of past design decisions.
* Solution: Provide **few-shot training examples** based on code usage, APIs, state transitions, or other specifications.
* Benefit: Examples can demonstrate proper usage and "train" the LLM on the fly.
* Challenge: Manually generating these examples may not be feasible.

### Structure and Key Ideas

The pattern generally follows these steps:

* Inform the LLM that you will provide "system X."
* Instruct the LLM to "Create a set of N examples that demonstrate usage of system X."
* Emphasise that examples should have "as complete as possible in their coverage."
* (Optional) Specify that "The examples should be based on the public interfaces of system X."
* (Optional) Direct the LLM to "The examples should focus on X" (a specific aspect).

### Example Implementation

* **REST API Example:** Prompt the LLM to "Create a set of 10 examples that demonstrate usage of this OpenAPI specification related to registration of new users."
  * These examples can later remind the LLM of the API's user creation design.
  * Can be more concise and convey more meaning than natural language.
* **General Code Example:** Prompt the LLM to "Create a set of 10 examples that demonstrate usage of this code. Make the examples as complete as possible in their coverage. The examples should be based on the public interfaces of the code."
  * Code examples are **information-rich** and **token-efficient**.
  * Effectively convey details like operation ordering and required data, which would be verbose in natural language.

### Consequences

* Can be used early in the design cycle to capture expected system usage and later provide usage-based explanations back to the LLM.
* Works well with patterns like the API Simulator pattern for rapid interaction recording and example generation.
* When example usage conveys critical information (constraints, assumptions, expectations) that would be more token-intensive to express otherwise.
* Even if not the most token-efficient method, example usage has been shown to be effective for LLM problem-solving.

### Example

```text
> User:

I am going to provide you with a Python function. I need you to create a set of 5 distinct code examples that demonstrate how to use this function. Make the examples as complete as possible in their coverage, showing different combinations of arguments and expected outputs. The examples should be runnable and clearly illustrate the function's behaviour. Here is the Python function:

def format_name(first_name: str, last_name: str, middle_initial: str = None, formal: bool = False) -> str:
    """
    Formats a given name based on provided parameters.

    Args:
        first_name: The person's first name.
        last_name: The person's last name.
        middle_initial: Optional. The person's middle initial.
        formal: Optional. If True, formats as "Last, First M." otherwise "First M. Last".

    Returns:
        A formatted string of the name.
    """
    if formal:
        if middle_initial:
            return f"{last_name}, {first_name} {middle_initial.upper()}."
        else:
            return f"{last_name}, {first_name}"
    else:
        if middle_initial:
            return f"{first_name} {middle_initial.upper()}. {last_name}"
        else:
            return f"{first_name} {last_name}"

Generate the 5 examples now.

> Gemini:

I will generate five distinct Python code examples that demonstrate the format_name function, covering various combinations of arguments and illustrating the expected outputs.

# --- Code Examples Demonstrating format_name Function ---

print("--- Example 1: Basic Informal Format ---")
# Description: Demonstrates the default informal formatting without a middle initial.
# Expected Output: "John Doe"
name1 = format_name("John", "Doe")
print(f"Input: first_name='John', last_name='Doe'")
print(f"Output: '{name1}'\n")

print("--- Example 2: Informal Format with Middle Initial ---")
# Description: Demonstrates informal formatting including a middle initial.
# The middle initial should be converted to uppercase.
# Expected Output: "Jane A. Smith"
name2 = format_name("Jane", "Smith", middle_initial="a")
print(f"Input: first_name='Jane', last_name='Smith', middle_initial='a'")
print(f"Output: '{name2}'\n")

print("--- Example 3: Basic Formal Format ---")
# Description: Demonstrates formal formatting without a middle initial.
# Expected Output: "Brown, Charlie"
name3 = format_name("Charlie", "Brown", formal=True)
print(f"Input: first_name='Charlie', last_name='Brown', formal=True")
print(f"Output: '{name3}'\n")

print("--- Example 4: Formal Format with Middle Initial ---")
# Description: Demonstrates formal formatting including a middle initial.
# The middle initial should be converted to uppercase.
# Expected Output: "Williams, Alice P."
name4 = format_name("Alice", "Williams", middle_initial="p", formal=True)
print(f"Input: first_name='Alice', last_name='Williams', middle_initial='p', formal=True")
print(f"Output: '{name4}'\n")

print("--- Example 5: Informal Format with Different Middle Initial Case ---")
# Description: Shows that the middle initial is always converted to uppercase,
# even if provided in lowercase for informal format.
# Expected Output: "Robert K. Johnson"
name5 = format_name("Robert", "Johnson", middle_initial="k")
print(f"Input: first_name='Robert', last_name='Johnson', middle_initial='k'")
print(f"Output: '{name5}'\n")

print("--- Example 6: Formal Format with Different Middle Initial Case ---")
# Description: Shows that the middle initial is always converted to uppercase,
# even if provided in lowercase for formal format.
# Expected Output: "Davis, Emily X."
name6 = format_name("Emily", "Davis", middle_initial="x", formal=True)
print(f"Input: first_name='Emily', last_name='Davis', middle_initial='x', formal=True")
print(f"Output: '{name6}'\n")

The Python code above provides six distinct examples demonstrating the format_name function. Each example showcases different combinations of arguments, including the presence/absence of middle_initial and the formal flag, along with their respective expected outputs. I've added an extra example (Example 6) to further highlight the middle initial case conversion in a formal context.
```

These concise examples can be used in future prompts to the LLM without needing to provide the full function definition again. (Imagine that the full function, or even module, is a lot longer than the example above.)

Scenario: A software engineer wants the LLM to write a test suite for the `format_name` function. Instead of including the function's code, they include the previously generated examples.

```text
> User:

I need you to write a Python unit test suite using pytest for a function that formats names. I will provide you with examples of how this function is used and its expected output. Use these examples as the basis for your test cases.

Here are the usage examples:

print("--- Example 1: Basic Informal Format ---")
# Description: Demonstrates the default informal formatting without a middle initial.
# Expected Output: "John Doe"
name1 = format_name("John", "Doe")
print(f"Input: first_name='John', last_name='Doe'")
print(f"Output: '{name1}'\n")

print("--- Example 2: Informal Format with Middle Initial ---")
# Description: Demonstrates informal formatting including a middle initial.
# The middle initial should be converted to uppercase.
# Expected Output: "Jane A. Smith"
name2 = format_name("Jane", "Smith", middle_initial="a")
print(f"Input: first_name='Jane', last_name='Smith', middle_initial='a'")
print(f"Output: '{name2}'\n")

print("--- Example 3: Basic Formal Format ---")
# Description: Demonstrates formal formatting without a middle initial.
# Expected Output: "Brown, Charlie"
name3 = format_name("Charlie", "Brown", formal=True)
print(f"Input: first_name='Charlie', last_name='Brown', formal=True")
print(f"Output: '{name3}'\n")

print("--- Example 4: Formal Format with Middle Initial ---")
# Description: Demonstrates formal formatting including a middle initial.
# The middle initial should be converted to uppercase.
# Expected Output: "Williams, Alice P."
name4 = format_name("Alice", "Williams", middle_initial="p", formal=True)
print(f"Input: first_name='Alice', last_name='Williams', middle_initial='p', formal=True")
print(f"Output: '{name4}'\n")

print("--- Example 5: Informal Format with Different Middle Initial Case ---")
# Description: Shows that the middle initial is always converted to uppercase,
# even if provided in lowercase for informal format.
# Expected Output: "Robert K. Johnson"
name5 = format_name("Robert", "Johnson", middle_initial="k")
print(f"Input: first_name='Robert', last_name='Johnson', middle_initial='k'")
print(f"Output: '{name5}'\n")

print("--- Example 6: Formal Format with Different Middle Initial Case ---")
# Description: Shows that the middle initial is always converted to uppercase,
# even if provided in lowercase for formal format.
# Expected Output: "Davis, Emily X."
name6 = format_name("Emily", "Davis", middle_initial="x", formal=True)
print(f"Input: first_name='Emily', last_name='Davis', middle_initial='x', formal=True")
print(f"Output: '{name6}'\n")

> Gemini

I've created a Python unit test suite using pytest for the format_name function, incorporating all the examples you provided as individual test cases.

import pytest

def test_basic_informal_format():
    """
    Test case for Example 1: Basic Informal Format.
    Expected Output: "John Doe"
    """
    assert format_name("John", "Doe") == "John Doe"

def test_informal_format_with_middle_initial():
    """
    Test case for Example 2: Informal Format with Middle Initial.
    The middle initial should be converted to uppercase.
    Expected Output: "Jane A. Smith"
    """
    assert format_name("Jane", "Smith", middle_initial="a") == "Jane A. Smith"

def test_basic_formal_format():
    """
    Test case for Example 3: Basic Formal Format.
    Expected Output: "Brown, Charlie"
    """
    assert format_name("Charlie", "Brown", formal=True) == "Brown, Charlie"

def test_formal_format_with_middle_initial():
    """
    Test case for Example 4: Formal Format with Middle Initial.
    The middle initial should be converted to uppercase.
    Expected Output: "Williams, Alice P."
    """
    assert format_name("Alice", "Williams", middle_initial="p", formal=True) == "Williams, Alice P."

def test_informal_format_with_different_middle_initial_case():
    """
    Test case for Example 5: Informal Format with Different Middle Initial Case.
    Shows that the middle initial is always converted to uppercase,
    even if provided in lowercase for informal format.
    Expected Output: "Robert K. Johnson"
    """
    assert format_name("Robert", "Johnson", middle_initial="k") == "Robert K. Johnson"

def test_formal_format_with_different_middle_initial_case():
    """
    Test case for Example 6: Formal Format with Different Middle Initial Case.
    Shows that the middle initial is always converted to uppercase,
    even if provided in lowercase for formal format.
    Expected Output: "Davis, Emily X."
    """
    assert format_name("Emily", "Davis", middle_initial="x", formal=True) == "Davis, Emily X."

# You can run these tests by saving the code above as `test_name_formatter.py`
# and then running `pytest` in your terminal from the same directory.
```

Explanation of implementation:

* **Token Efficiency:** The software engineer did not need to paste the entire `format_name` function code into the prompt. The 6 lines of generated examples (plus comments) were significantly fewer tokens than the function's definition and docstrings. (The generated examples above as a whole is actually longer than the function code, but imagine that we are dealing with a much longer function or module.) This is crucial for larger codebases or more complex APIs where full code might hit token limits.
* **Contextual Understanding:** The examples provided concrete, runnable scenarios that effectively conveyed the function's behaviour to the LLM. This allowed the LLM to understand what constitutes a "correct" output for various inputs without requiring explicit natural language descriptions of all edge cases.
* **Reduced Ambiguity:** By providing exact inputs and expected outputs, the LLM had a much clearer target for its test generation than if the software engineer had simply said, "write tests for a name formatting function."
* **Reusability:** The generated examples are a valuable asset. The software engineer could save them (e.g., in a `usage_examples.py` file or a documentation markdown) and use them in other LLM interactions (e.g., "generate documentation for this function based on these examples," or "suggest improvements to this function based on these common usage patterns").

### Discussion

* It can be similarly beneficial to generate the usage examples in the form of test cases.
  * Software developers should already be familiar with the syntax of test cases and therefore they should be as readable as regular usage examples.
* Test cases have the additional benefits such as:
  * being directly executable to check that the generated examples (test cases) are in fact generated correctly;
  * more naturally demonstrating edge cases, boundary conditions, and error handling;
  * if subsequent task is anything related to validation, verification, or robustness, test-case-style examples provide a much stronger and more explicit signal about what constitutes "correctness";
  * if the LLM is pre-trained on a lot of test code (in that specific programming language and test framework), it will deeply understand the semantic meaning of assertions, allowing it to better reason about expected behaviour.
* However, if usage examples are being generated for a REST API, for example, then regular usage examples are generally more readable and succinct than test cases.

## Prompts

* The following describes the Few-Shot Code Example Generation prompt pattern. It has 5 main sections: (1) Intent and Context, (2) Motivation, (3) Structure and Key Ideas, (4) Example Implementation, and (5) Consequences. Summarise it in bullet points form, section by section. [Text of the pattern]

## Source

* White, J., Hays, S., Fu, Q., Spencer-Smith, J., & Schmidt, D. C. (2023). _ChatGPT Prompt Patterns for Improving Code Quality, Refactoring, Requirements Elicitation, and Software Design._ ArXiv.org. <https://arxiv.org/abs/2303.07839>
