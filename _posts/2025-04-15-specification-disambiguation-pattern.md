---
layout: post
title: Specification Disambiguation Pattern
categories: ai llm pattern software
published: true
plantuml: false
---

The Specification Disambiguation Pattern, a prompt pattern to review specifications provided to a developer or development team.

This summary is mostly generated using Google Gemini from an academic paper (see Source below). The example at the end is from an actual interaction with Google Gemini (2.0 Flash).

## Specification Disambiguation Pattern

### Intent and Context

* Aims to have an LLM review specifications, often from non-technical or semi-technical personnel.
* Goal is to identify and clarify potential miscommunication or ambiguity early in the process.

### Motivation

* Software developers frequently work with product/project managers who gather requirements.
* Meaningful context can be lost during the capture and delivery of these requirements (often stemming from customer discussions).
* This pattern helps automate the disambiguation of requirements before they reach developers.

### Structure and Key Ideas

Fundamental contextual statements for the prompt:

1. Within this scope
2. Consider these requirements or specifications
3. Point out any areas of ambiguity or potentially unintended outcomes

### Example Implementation

* Scenario: Non-technical product manager captures customer requirements in natural language, unsuitable for precise software requirements.
* Product manager uses a prompt like: "The following will represent system requirements. Point out any areas that could be construed as ambiguous or lead to unintended outcomes. Provide ways in which the language can be more precise."
* LLM analyses provided requirements (e.g., file upload, security, file types, size limits).
* LLM identifies ambiguities and suggests more precise language, e.g.:
  * 'The system requirement to "Keep the files secure" could be made more precise by specifying which security measures should be implemented to ensure the files are kept secure. For example: "Implement access control and encryption measures to ensure that uploaded files can only be accessed by authorized users and are protected against unauthorized access or tampering."'
* Follow-up questions such as "provide example requirements for a system that accepts file uploads by logged-in users, and keeps the files secure the entire time" can further guide the product manager towards clearer requirements.

### Consequences

* Difficulty: Errors, ambiguities, or omissions in specifications are often found late in the development cycle.
* Developers may make assumptions to implement ambiguous ideas, which might not align with the original intent.
* This pattern acts as an automated "devil's advocate" to find weaknesses in specifications.
* LLMs overcome social concerns (such as the concern of questioning a more senior developer) that might prevent developers from questioning specifications.
* Useful for integrating separate systems with a common specification, allowing teams to identify ambiguities independently that can then be brought up for discussion.
* Beneficial when developing specifications for external audiences where direct feedback is difficult to obtain.
* Effective when combined with other patterns like Persona, API Generator, API Simulator, and Requirements Simulator to uncover further ambiguities through different perspectives and transformations.

### Example

```text
User:
The following are requirements for a software application that allows users to upload files. Point out any areas that could be construed as ambiguous or lead to unintended outcomes. Provide ways in which the language can be more precise.

1. The application shall provide a clear and intuitive way for users to select files for uploading through a standard web browser interface.
2. The system should handle file uploads efficiently.
3. Users must be able to upload various types of files.
4. The application will ensure the uploaded files are stored securely.
5. There should be a mechanism to track all file uploads.
6. The application needs to be user-friendly.

Gemini:
Alright, let's break down these requirements and pinpoint the ambiguities:

* Requirement 1: "The application shall provide a clear and intuitive way for users to select files for uploading through a standard web browser interface."
    * Potential Ambiguity: While "clear and intuitive" is a good goal, it's subjective. What one user finds intuitive, another might not. "Standard web browser interface" is generally understood, but could there be specific browser compatibility requirements?
    * More Precise Language: "The application shall allow users to select files for upload using the standard file input element (`<input type='file'>`) supported by the latest two major versions of Chrome, Firefox, Safari, and Edge browsers. The file selection process should involve a single file dialog or a drag-and-drop zone clearly visible on the upload page."

* Requirement 2: "The system should handle file uploads efficiently."
    * Potential Ambiguity: "Efficiently" is very vague. What constitutes an acceptable upload speed? What are the resource constraints (CPU, memory, network bandwidth) under which this efficiency should be maintained?
    * More Precise Language: "The system shall be able to handle file uploads up to 100MB in size within 5 seconds on a network with a minimum upload speed of 10 Mbps, with average CPU utilization on the server not exceeding 60% during peak upload times." (Note: Specific numbers here are examples and would need to be defined based on actual needs).

* Requirement 3: "Users must be able to upload various types of files."
    * Potential Ambiguity: "Various" is not specific. Does it include all file types? Are there any restrictions (e.g., executable files, system files)? What about maximum file size per type?
    * More Precise Language: "The system shall support the upload of the following file types: .jpg, .jpeg, .png, .gif, .pdf, .doc, and .docx, with a maximum file size of 50MB per file, regardless of type. The system should reject uploads of other file types and display an informative error message to the user."

* Requirement 4: "The application will ensure the uploaded files are stored securely."
    * Potential Ambiguity: "Securely" is broad. What specific security measures will be implemented? Will the files be encrypted at rest? What about access control? How will unauthorized access be prevented?
    * More Precise Language: "Uploaded files shall be encrypted at rest using AES-256 encryption. Access to the stored files shall be role-based, with only authorized users having access to files they have uploaded or files explicitly shared with them. Regular security audits will be conducted to ensure the integrity of the stored files."

* Requirement 5: "There should be a mechanism to track all file uploads."
    * Potential Ambiguity: What information will be tracked? Who will have access to this tracking information? How long will this information be retained? What is the purpose of tracking?
    * More Precise Language: "The system shall maintain a log of all file uploads, including the user who uploaded the file, the filename, the upload timestamp, and the file size. This log shall be accessible to administrators only and retained for a period of 12 months for auditing and support purposes."

* Requirement 6: "The application needs to be user-friendly."
    * Potential Ambiguity: "User-friendly" is highly subjective. What specific usability criteria will be met? Will there be user testing? What are the key tasks users need to perform easily?
    * More Precise Language: "The application shall adhere to common web usability guidelines, including clear labeling of all interactive elements, consistent navigation, and providing informative feedback to the user upon successful or failed uploads. User testing with at least five representative users should be conducted to identify and address any usability issues before final deployment."

By making the language more specific, we reduce the chances of misinterpretation and ensure that the development team has a clearer understanding of the intended functionality and quality attributes of the file upload application.
```

## Prompts

* The following describes the Specification Disambiguation Pattern. It has 5 main sections: (1) Intent and Context, (2) Motivation, (3) Structure and Key Ideas, (4) Example Implementation, and (5) Consequences. Please summarise it in bullet points form, section by section. [Text of the pattern]

## Source

* White, J., Hays, S., Fu, Q., Spencer-Smith, J., & Schmidt, D. C. (2023). _ChatGPT Prompt Patterns for Improving Code Quality, Refactoring, Requirements Elicitation, and Software Design._ ArXiv.org. <https://arxiv.org/abs/2303.07839>
