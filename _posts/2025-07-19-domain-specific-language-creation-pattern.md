---
layout: post
title: Domain-Specific Language (DSL) Creation Pattern
categories: ai llm pattern software
published: true
plantuml: false
---

The Domain-Specific Language (DSL) Creation Pattern enables an LLM to generate a custom, token-efficient language for specific system concepts, which both the LLM and users can leverage for clearer and more concise communication.

This summary is mostly generated using Google Gemini from an academic paper (see Source below). The example at the end is from an actual interaction with Google Gemini (2.5 Flash), modified slightly for clarity and brevity.

## Domain-Specific Language (DSL) Creation Pattern

### Intent and Context

* Enables an **LLM to create its own DSL**.
* Both the **LLM and users can use the DSL** to describe and manipulate system concepts (e.g., requirements, deployment, security rules, architecture).
* The LLM can **design and describe the DSL to users**.
* LLM-generated examples and descriptions can be **stored and reused in future prompts** to reintroduce the DSL.
* Generated examples also serve as **few-shot examples** for future prompts.

### Motivation

* **DSLs offer succinct and token-efficient formats** compared to natural language or programming languages.
* LLMs have **maximum token limits** for prompts, making token-efficient inputs crucial for large software projects.
* Creating a DSL can be **time-consuming**, especially describing its syntax and semantics (metamodel) to the LLM beforehand.

### Structure and Key Ideas

The fundamental contextual statements for the DSL Creation Pattern are:

* "I want you to create a domain-specific language for X"
* "The syntax of the language must adhere to the following constraints"
* "Explain the language to me and provide some examples"

### Example Implementation

* A sample implementation for **creating a DSL for requirements** includes the constraint that the syntax should be "YAML-like."
  * Example prompt: "I want you to create a domain-specific language to document requirements. The syntax of the language should be based on YAML. Explain the language to me and provide some examples."
  * "YAML-like" may result in syntax that looks similar but isn't strictly valid YAML.
* Another approach involves asking the LLM to create **a set of related DSLs with references between them**.
  * This is useful for describing related system aspects and tracing concepts across DSL instances (e.g., tracing requirements to architectural modules).
  * The LLM can be instructed to **link concepts with consistent identifiers** for cross-DSL tracking.

### Consequences

* Can **facilitate system design without hitting token limits**.
* **Careful consideration of syntax rules** given to the LLM is crucial, as they directly influence the space-efficiency of the generated DSL.
  * High concept-density in a DSL may not always translate to token-efficiency in its textual representation (e.g., XML-based syntax is often less space-efficient than YAML-based).
* **Token efficiency can be improved via conventions and implicit syntax rules** (e.g., positional conventions in a list).
  * **Downside**: DSL may be harder for unfamiliar users to interpret.
  * This can be **rectified by using the Few-shot Code Example Generation pattern** to create examples that teach users the DSL.
  * Combining these patterns helps the LLM **self-document DSL usage** for later prompts.

### Example

```text
> User:

I want you to create a domain-specific language to document software requirements. The syntax of the language should be based on YAML. Explain the language to me and provide some examples.

> Gemini:

A Domain-Specific Language (DSL) based on YAML for software requirements can offer a clear, human-readable, and machine-parsable way to document system functionalities, constraints, and user interactions. YAML's hierarchical structure is well-suited for organizing the various aspects of a requirement.

Here's a proposed DSL for software requirements, named "ReqFlow," along with explanations and examples.

-----

ReqFlow: A YAML-based DSL for Software Requirements

ReqFlow aims to capture essential information about software requirements in a structured yet flexible manner. It emphasizes clarity, traceability, and maintainability.

Core Concepts and Structure

At its highest level, a ReqFlow document will be a list of requirements, where each requirement is a YAML object.

Top-Level Structure

- Requirement:
    id: REQ-001
    title: User Authentication
    status: Approved
    priority: High
    type: Functional
    description: |
      Users must be able to securely log in to the system using their registered credentials.
    actors:
      - User
      - System
    preconditions:
      - User has a registered account.
      - User has an active internet connection.
    postconditions:
      - User is successfully authenticated.
      - User is redirected to the dashboard.
    scenarios:
      - scenario_name: Successful Login
        steps:
          - step: User enters valid username and password.
            actor: User
          - step: System validates credentials.
            actor: System
          - step: System grants access.
            actor: System
          - step: User is redirected to dashboard.
            actor: User
        expected_result: User is logged in.
      - scenario_name: Invalid Credentials
        steps:
          - step: User enters invalid username or password.
            actor: User
          - step: System displays "Invalid credentials" error message.
            actor: System
        expected_result: Error message displayed.
    non_functional_constraints:
      - type: Performance
        description: Login process must complete within 2 seconds.
      - type: Security
        description: Passwords must be hashed and salted.
    traceability:
      user_story: US-001
      epics:
        - EPIC-001
      design_docs:
        - DD-AUTH-001
    attachments:
      - type: Diagram
        path: auth_flow.png
      - type: Mockup
        path: login_screen.fig
    notes: |
      Initial implementation will support email/password login. Social logins (Google, Facebook)
      will be considered in a later phase.

Detailed Explanation of Fields

Here's a breakdown of the fields within a `Requirement` object:

* `id` (String, Required): A unique identifier for the requirement. This is crucial for traceability and referencing.
    * Example: `REQ-001`, `NF-005`
* `title` (String, Required): A concise, descriptive title for the requirement.
    * Example: `User Registration`, `Database Backup`
* `status` (String, Optional): The current status of the requirement (e.g., `Draft`, `Approved`, `In Progress`, `Implemented`, `Tested`, `Rejected`).
    * Example: `Approved`
* `priority` (String, Optional): The importance or urgency of the requirement (e.g., `Critical`, `High`, `Medium`, `Low`).
    * Example: `High`
* `type` (String, Optional): Categorization of the requirement (e.g., `Functional`, `Non-Functional`, `Usability`, `Performance`, `Security`, `Regulatory`).
    * Example: `Functional`
* `description` (Multi-line String, Required): A detailed explanation of what the requirement entails. This should be clear, unambiguous, and comprehensive. Markdown can be used for formatting within the multi-line string.
    * Example: See the example above.
* `actors` (List of Strings, Optional): The entities (users, systems, external services) that interact with or are affected by this requirement.
    * Example: `User`, `Admin`, `Payment Gateway`
* `preconditions` (List of Strings, Optional): Conditions that must be true before the requirement can be fulfilled or a scenario can begin.
    * Example: `User is logged in`, `System has internet access`
* `postconditions` (List of Strings, Optional): Conditions that are true after the requirement is fulfilled or a scenario completes successfully.
    * Example: `Data is saved`, `User receives confirmation email`
* `scenarios` (List of Objects, Optional): Use cases or user stories detailing the steps involved in fulfilling the requirement. Each scenario can have:
    * `scenario_name` (String, Required): A brief name for the scenario.
    * `steps` (List of Objects, Required): A sequential list of actions.
        * `step` (String, Required): Description of the action.
        * `actor` (String, Optional): The actor performing the step.
    * `expected_result` (String, Required): The anticipated outcome of the scenario.
* `non_functional_constraints` (List of Objects, Optional): Specific non-functional requirements or constraints related to this functional requirement.
    * `type` (String, Required): The type of non-functional constraint (e.g., `Performance`, `Security`, `Usability`, `Reliability`).
    * `description` (String, Required): The specific constraint.
* `traceability` (Object, Optional): Links to other development artifacts for traceability.
    * `user_story` (String, Optional): Link to a user story ID (e.g., from a backlog management tool).
    * `epics` (List of Strings, Optional): Link to epic IDs.
    * `design_docs` (List of Strings, Optional): References to related design documents.
    * Other custom fields can be added here as needed.
* `attachments` (List of Objects, Optional): References to external files or resources that further explain or illustrate the requirement.
    * `type` (String, Required): The type of attachment (e.g., `Diagram`, `Mockup`, `Specification`).
    * `path` (String, Required): The file path or URL to the attachment.
* `notes` (Multi-line String, Optional): Any additional comments, considerations, or open questions related to the requirement.

Advantages of ReqFlow

* Human-Readable: YAML's syntax is easy for humans to read and understand, even for non-technical stakeholders.
* Machine-Parsable: The structured nature of YAML makes it straightforward to parse and process programmatically. This enables:
    * Automated generation of documentation: Tools can read ReqFlow files and generate various reports (e.g., requirement matrices, test plans).
    * Integration with other tools: Requirements can be easily imported into ALM (Application Lifecycle Management) tools, test management systems, or issue trackers.
    * Validation: Tools can validate ReqFlow files against a schema to ensure consistency and correctness.
* Version Control Friendly: YAML files are plain text, making them ideal for version control systems like Git. This allows for tracking changes, reviewing revisions, and collaborating effectively.
* Extensible: The DSL can be easily extended by adding new fields or refining existing ones to meet specific project needs without breaking existing structures.
* Hierarchical Structure: Naturally supports breaking down complex requirements into smaller, manageable parts.

Example Scenarios

1. Functional Requirement: User Registration

- Requirement:
    id: REQ-002
    title: User Registration
    status: Approved
    priority: High
    type: Functional
    description: |
      The system must allow new users to register an account by providing a unique email address,
      a username, and a password. Upon successful registration, a confirmation email should be sent.
    actors:
      - New User
      - System
    preconditions:
      - System is online.
      - User has access to an email client.
    postconditions:
      - New user account is created and stored in the database.
      - Confirmation email is sent to the user's registered email address.
    scenarios:
      - scenario_name: Successful Registration
        steps:
          - step: User navigates to the registration page.
            actor: New User
          - step: User enters unique email, username, and password.
            actor: New User
          - step: User clicks "Register" button.
            actor: New User
          - step: System validates input and creates account.
            actor: System
          - step: System sends confirmation email.
            actor: System
          - step: System redirects user to a "Registration Successful" page.
            actor: System
        expected_result: User account created, confirmation email sent, user redirected to success page.
      - scenario_name: Email Already Registered
        steps:
          - step: User navigates to the registration page.
            actor: New User
          - step: User enters an email address already registered.
            actor: New User
          - step: User clicks "Register" button.
            actor: New User
          - step: System displays "Email already registered" error message.
            actor: System
        expected_result: Error message displayed, account not created.
    non_functional_constraints:
      - type: Security
        description: Passwords must be stored using a strong hashing algorithm (e.g., bcrypt).
      - type: Performance
        description: Registration process should complete within 3 seconds.
    traceability:
      user_story: US-002
      epics:
        - EPIC-001
    notes: |
      Consider adding CAPTCHA to prevent automated registrations.

2. Non-Functional Requirement: System Performance

- Requirement:
    id: NFR-001
    title: System Response Time
    status: Approved
    priority: High
    type: Non-Functional
    description: |
      All user-facing interactions and API calls must have a response time of less than 2 seconds
      under normal load conditions (up to 100 concurrent users).
    actors:
      - User
      - System
    non_functional_constraints:
      - type: Performance
        description: 95% of API calls must complete within 1 second.
      - type: Performance
        description: Page load times must not exceed 2 seconds for 90% of requests.
    traceability:
      epics:
        - EPIC-003 # System Performance Epic
      design_docs:
        - DD-ARCH-001 # System Architecture Document
    notes: |
      This requirement applies to all core functionalities, including login, data retrieval, and
      data submission.

Tooling Considerations

While ReqFlow defines the language, robust adoption would benefit from tooling, such as:

* Schema Validation: A JSON Schema or similar could be used to validate ReqFlow YAML files, ensuring they adhere to the defined structure.
* Parsers/Libraries: Libraries in various programming languages (Python, Java, JavaScript) could parse ReqFlow files into objects for further processing.
* Generators: Tools to generate HTML, PDF, or Markdown documentation from ReqFlow files.
* Integrations: Plugins or connectors for ALM tools (Jira, Azure DevOps), test management systems, and version control systems.

-----

This ReqFlow DSL provides a solid foundation for documenting software requirements in a structured, readable, and machine-friendly way, leveraging the simplicity and power of YAML.
```

## Prompts

* The following describes the Domain-Specific Language (DSL) Creation Pattern. It has 5 main sections: (1) Intent and Context, (2) Motivation, (3) Structure and Key Ideas, (4) Example Implementation, and (5) Consequences. Summarise it in bullet points form, section by section. [Text of the pattern]
* Provide a one-line summary of this pattern.

## Source

* White, J., Hays, S., Fu, Q., Spencer-Smith, J., & Schmidt, D. C. (2023). _ChatGPT Prompt Patterns for Improving Code Quality, Refactoring, Requirements Elicitation, and Software Design._ ArXiv.org. <https://arxiv.org/abs/2303.07839>
