---
layout: post
title: Introduction to Generative AI for Software Development
categories: ai llm development
published: true
plantuml: false
---

Summary of the Introduction to Generative AI for Software Development course at <https://www.coursera.org/learn/introduction-to-generative-ai-for-software-development/>.

## Pair-Coding with an LLM

### Transformers and Code

* Large language models (LLMs) can significantly aid in coding and development, transforming approaches to common programming challenges.
* LLMs, built on transformer architectures, excel at parallel data processing and precise context understanding, enabling them to analyze vast amounts of text quickly.
* Code Analysis and Improvement:
  * Scan codebases for syntax errors, bugs, and inefficiencies.
  * Suggest better algorithms and refactor code for performance enhancement.
  * Help trace execution to pinpoint errors, reducing debugging time.
* Dependency Management:
  * Analyze project files and code imports to suggest updates and identify incompatible versions, ensuring project stability and minimizing conflicts.
* Documentation Generation:
  * Automatically generate comments and documentation, improving code readability and maintainability.
* Technical Debt Management:
  * Review complex code to aid understanding and suggest refactoring/redesign strategies.
  * Prioritize debt reduction tasks for easier future maintenance.
* Creative Problem Solving and Innovation:
  * Brainstorm creative solutions to complex problems.
  * Propose innovative features.
  * Simulate integration of new modules with existing systems.
* Revolutionizing Development:
  * LLMs extend developer capabilities, allowing focus on creative and strategic aspects of development.

### Generating Code with Chatbots

* Adjust the prompts for each language, reflecting typical naming and syntax conventions, such as calling it a method in C#.
* It's the domain knowledge of the language, the APIs, and the supporting libraries that make you a better developer and will make you a better prompter.
* Also, the domain knowledge of the business problem you're trying to solve will give you better ways of expressing the solution in either prompts or code.
* By making your prompts more specific and detailed, specifying parameters and conditions helps the model to refine its output.
* Interactive coding to continuously update your code:
  * It doesn't have to be a one shot situation where you take the code from GPT and use it as is.
  * You can continue to prompt the model to create better code.
  * Example:
    * `Write a JavaScript function to check if a number is prime.`
    * `Update the function to include error handling for non-integer and non-positive inputs.`
* In general, vague prompts can lead to ambiguous outputs.
* When using prompts for code, or for anything else, you should:
  * be specific,
  * use clear language, and
  * provide as much context as necessary for the model to successfully complete the task.
* Example:

```text
Can you help me create a simple Flask application in Python that includes one API endpoint? This endpoint should handle GET requests at the URL /multiply, which accepts two query parameters a and b and returns the multiplication of these two parameters as a JSON response. Make sure to include error handling if the parameters are not provided or if they are convertible to integers.
```

* LLMs can help you debug code. Example:

```text
Help me find errors in this code:

def calculate_average(numbers):
    total_sum = sum(numbers)
  count = len(numbers)
  average = total_sum/count
  return average
```

* Example of an effective prompt:

```text
Please write a Python function named calculate_area that takes an argument radius.

The function should calculate the area of a circle given the radius. Ensure that the function handles non-numeric inputs by raising a ValueError with the message 'Input must be a numeric value.'

Include comments in the code explaining each step.
```

### Iterative Prompting

* Context is basically information in your prompt that can steer the LLM to a better answer.
* Example: You want a Python function to download a file and save it to disk with detailed context about how to do this like not using `wget`:

```text
Write a Python function using the requests library to download a file from a URL and save the file to disk without using third-party libraries like wget.
```

* You can refine the output of an LLM by iterating on the prompt.
* Example:
  * `Create a REST API in Flask to return user data.`
  * `Now add error handling to the API to handle 404 and 500 status codes.`
  * `Please add detailed comments explaining each part, including the complex sections.`
    * Good way to learn about the generated code if it is unfamiliar to you.

### Giving the LLM Feedback

* There's another nuance of re-prompting - incorporating feedback.
* It's a similar idea, but it's more about using your own expertise to spot and correct errors or deficiencies in the code.
  * Think of the code from an LLM as a first draft.
  * It's exceptionally rare for a first draft to be perfect, so it takes some work to guide the model to continually re-draft and get it right.
* Example:
  * `Write a Python function to calculate the factorial of a number.`
  * `Please modify the function to include a check that ensures the input is a non-negative integer.`
* Another example:
  * `Create a Python function to check if a string is a palindrome.`
  * `Update the code to ensure that the string isn't empty.`

### Assigning the LLM a Role

* By specifying a role for the model to assume in your prompts, you set expectations and guide its tone, level of detail, and the perspective from which it addresses the query.
* Depending on your level of expertise, you might want different code to be generated.
  * A beginner might want code that's easier to read.
  * An expert might want code that is shorter, compact, and more efficient.
* Example:
  * Without role: `Write a Python function to calculate a factorial.`
  * With role: `As my Python mentor, please write a function to calculate a factorial.`
* A role is the character or perspective that you assign to the AI.
  * This could be a tutor, a coach, a code reviewer, or even a fictional character.
* Example:
  * Without role: `Explain how to create a list in Python and add elements to it.`
  * With role: `As a beginner Python tutor, explain how to create a list in Python and add elements to it.`

### Levelling Up with Multiple Roles

* Combining roles can allow the model to create responses that are not only complex, but also incredibly insightful.
* Example:

```text
As both a software architect and security expert, evaluate this Python script for a web application and suggest architectural improvements and security enhancements.

dev store_user_data(user_data):
    database = open('user_database.txt', 'a')
    database.write(str(user_data))
    database.close()

store_user_data({'username': 'admin', 'password': '1234'})
```

### Expert Roles for Specialised Knowledge

* Get to the next level with roles by instructing GPT to be more than just a code generator.
* It should act as a key member of your developer team, offering insights based on the vast data that it's been trained on and bringing an experienced programmer's perspective to its responses.
* Example:

```text
As a contributor to open-source Python projects, critique this Python library for data visualisation and suggest enhancements to make it comparable to major libraries like Matplotlib or Seaborn.

import matplotlib.pyplot as plt

class DataVisualizer:

    def init(self, data):
        self.data = data

    def plot(self, kind='line'):
        if kind == 'line':
            plt.plot(self.data)
        elif kind == 'bar':
            plt.bar(range(len(self.data)), self.data)

        plt.show()

# Example usage
visualizer = DataVisualizer([10, 20, 30, 40, 50])
visualizer.plot('bar')
```

* By specifying this role, you expect the model to provide a detailed critique on the features, performance, and usability of your code and to suggest specific improvements.
* Example (compare responses without and with “as an NLP expert”):

```text
As an NLP expert, suggest improvements to this text summarization feature to enhance its functionality and accuracy.

import nltk

class TextAnalyzer:

    def __init__(self, text):
        self.text = text

    def summarize(self):
        sentences = nltk.senttokenize(self.text)
        return ' '.join(sentences[:2])
```

* Here, you're encouraging the model to not just critique, but also provide suggestions for applying state of the art NLP techniques to improve the functionality of your app.
* Example (compare responses without and with “as a software tester”):

```text
As a software tester, analyze this function for potential edge cases and suggest robust handling strategies.

def calculated_discount(price, discount):
    if discount > 100:
        raise ValueError('Discount cannot exceed 100%')

    return price * (100 - discount) / 100

# Test cases
print(calculated_discount(100, 105)) # Should raise an exception
```

### Best practices

* Be specific
  * Provide detail and context about your problem.
  * The more specific your prompt, the better the response you'll get.
* Assign a role
  * Experiment with different roles to see what gets you the output that you need.
* Request an expert opinion
  * Assign an expert role and ask the LLM to evaluate the work you've already done to further refine it.
* Give feedback
  * Iteratively prompt the LLM and provide feedback on the output you receive to get closer to your expected results.
  * Most interactions with an LLM will require a few back and forth prompts before you get to something that you're ready to actually try using.

#### Getting the most out of LLMs

* Experiment with what your LLM can do.
  * Set aside time to try out different tasks that an LLM can help you with
  * Intentionally push the limits of what it can do.
    * Can it understand the most complex parts of your code base?
    * Can it refactor an entire library?
  * Even if some of those experiments fail, approaching LLMs with an attitude of curiosity will help you uncover new possibilities.
* Test your LLM code carefully.
  * Avoid the temptation to just copy and paste LLM generated code into your project and move on.
  * Review what was written and test it to ensure that the code not only works well, but it's compatible with the rest of your code base.
* Use LLMs as a learning tool.
  * LLMs can suggest designs, software libraries, or even broader approaches that you wouldn't have considered.
  * You can always ask follow-up questions, request example code, or just have the model present pros and cons of the solutions that it provides.
* You are the context expert.
  * Ultimately, you still need to be the one that critically evaluates the code that's been written, and decides whether it fits the needs of your project.

## Leveraging an LLM for Code Analysis

### Arrays

* To analyse the suitability of and issues with using an array:
  * `What would happen if I had nothing in my Python array?`
  * `What would happen if I had billions of numbers in my Python array?`
  * `What risks would I have implementing billions of numbers using an array?`
  * `Take on the role of an expert software engineer, what advice would you give me in using an array like this?`

### Linked Lists

* It's easy to have an LLM implement code for you, but if you don't understand why the model decided on a particular implementation, you can make bad decisions that accumulate technical debt.
* As you work to write code with an LLM, be sure to quiz the model about why it's making the recommendations that it does.
* To analyse the performance of linked lists:
  * `Write some code to implement a linked list in Python.`
  * `What are the downsides and overheads associated with linked lists compared to other Python data structures?`
  * `Take on the role of an expert software developer at a company that suffers from denial of service attacks. If I implement some routines with code like this, what risks am I facing?`
  * `How would you modify the code to mitigate against these?`
* LLMs can help you analyse and think deeply about your code.

### Trees

* Analysing the performance of trees:

```python
class TreeNode:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key


class BinaryTree:
    def __init__(self):
        self.root = None

    def insert(self, key):
        if self.root is None:
            self.root = TreeNode(key)
        else:
            self._insert(self.root, key)

    def _insert(self, node, key):
        if key < node.val:
            if node.left is None:
                node.left = TreeNode(key)
            else:
                self._insert(node.left, key)
        else:
            if node.right is None:
                node.right = TreeNode(key)
            else:
                self._insert(node.right, key)

    def inorder(self, node):
        if node:
            self.inorder(node.left)
            print(node.val, end=" ")
            self.inorder(node.right)


# Example usage
bt = BinaryTree()
bt.insert(8)
bt.insert(3)
bt.insert(10)
bt.insert(1)
bt.insert(6)
bt.insert(4)
bt.insert(7)

print("Inorder traversal of the binary tree:")
bt.inorder(bt.root)

```

* `You are an expert software engineer and site reliability engineer that puts code into production in large scale systems. I have an implementation of a binary search tree here - please analyze it and let me know what I would need to do to trust this in a production environment, particularly from a security perspective. Also, is there anything missing I should add?`
* `Can you update the code to fix all of the security considerations, while also adding the functional enhancement? Please thoroughly document this code line by line to explain what each line does. Be very detailed, in particular for the recursive and threaded parts.`

### Graphs

* `Implement a simple graph data structure in Python.`
* `Please comment this code thoroughly.`
* `This code doesn't appear to do a directed graph -- a is connected to b, but b is not connected to a -- plesae fix it.`
* `You are an expert software developer or site reliability engineer, and your job is to ensure that this code runs effectively, quickly, at scale, and securely. Please profile it, and find any issues that need to be fixed or updated.`
* `Please go through and edit the code to implement the recommendations, add input validation, and make it as memory efficient as possible.`

### Hash tables and maps

* `Please write plain Python code using the base language to download text from a given URL, and then count every instance of every word in that text.`
  * Produces code that uses `Counter` from the `collections` module.
* `I'm not familiar with Counter in Python. Please explain what it is.`
* `Why did you use a Counter to do this, instead of just a Python dictionary?`
* `Say I had millions of URLs that I needed to count the words in. Does Counter scale better than dictionary for that?`
* `I see you use a regular expression to break the corpus into extra words. Is this the fastest and most scalable way? What if there were millions of books instead of just one?`
* No size fits all and bringing your expertise about your system to understand the problem is vital.
* Working with an LLM like this can throw up some great ideas, but they're not necessarily always the right ideas for your specific system.

