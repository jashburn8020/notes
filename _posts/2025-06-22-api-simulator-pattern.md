---
layout: post
title: API Simulator Pattern
categories: ai llm pattern software
published: true
plantuml: false
---

The API Simulator Pattern, a prompt pattern to simulate an API based on a specification provided by a developer or a development team.

This summary is mostly generated using Google Gemini from an academic paper (see Source below). The example at the end is from an actual interaction with Google Gemini (2.5 Flash).

## API Simulator Pattern

### Intent and Context

* Causes the LLM to simulate an API based on its specification.
* Utilises LLMs for generating synthetic data tailored to natural language descriptions of scenarios.
* LLMs can synthesise sample requests, provide usage guidance, and explain errors.

### Motivation

* Traditional API simulation tools require setup and may have limited synthetic data generation capabilities.
* Supports a more flexible interface using pseudo-operations and concrete operation specifications, unlike strict HTTP or code-based interactions.
* Allows developers to uncover problems, omissions, or awkward designs during early API interaction.

### Structure and Key Ideas

The fundamental contextual statements are:

* Act as the described system using specification X.
* I will type in requests to the API in format Y.
* You will respond with the appropriate response in format Z based on specification X.

### Example Implementation

* An example involves asking the LLM to simulate a REST API based on an OpenAPI specification.
* Requests are typed as HTTP requests, and the LLM outputs HTTP responses.
* The LLM can also generate descriptions of state changes, and user input can be a description of user actions with the API or a web client.
* Specifications can be programmatic interfaces or common API specification domain-specific languages (e.g., OpenAPI).

### Consequences

* Users can easily customise scenarios (e.g., "assume the user has a valid OAuth token," "assume 100 users exist") using natural language.
* Interactions can be rigorous (e.g., "strictly interpret my input as an HTTP request") or more lenient (e.g., "I will only provide pseudo data, fix formatting issues").
* The flexibility in interaction and customisation speeds up API exploration.
* The LLM can create usage examples for future prompts or help users assess task difficulty in code.
* Can be combined with patterns like "Change Request Simulation" to reason about effort needed for accommodating changing assumptions.

### Example

An OpenAPI specification was generated for this example using the following prompt:

```text
Generate an OpenAPI 3.0.0 specification for a REST API that is strictly compliant with RFC 9110. The API should implement the requirements below. Keep the API simple. Include in the specification an example where the wishlist already contains 3 products. Once you have generated the specification, check the specification to make sure it is strictly compliant with RFC 9110.

- As a user, I want to see all the products that I have added to my wishlist so that I can decide whether to keep or remove the products on my wishlist.
- As a user, I want to add products onto my wishlist so that I can quickly find and buy the product later.
- As a user, I want to remove products from my wishlist so that I can keep my wishlist only for products that I may want to buy later.
```

The following shows an LLM simulating an API based on a specification.

```text
User:
Act as a REST API based on the OpenAPI specification below. I will type in HTTP requests in plain text and you will respond with the appropriate HTTP response based on the specification.

openapi: 3.0.0
info:
  title: Wishlist API
  description: |
    API for managing user wishlists.
    This API strictly adheres to the principles outlined in RFC 9110 for HTTP semantics.
  version: 1.0.0
servers:
  - url: https://api.example.com/v1
    description: Production server
tags:
  - name: Wishlist
    description: Operations related to a user's product wishlist.

paths:
  /wishlist:
    get:
      summary: Retrieve user's wishlist
      description: |
        Retrieves all products currently in the user's wishlist.
        This operation is safe and idempotent, as per RFC 9110.
      operationId: getWishlist
      tags:
        - Wishlist
      responses:
        '200':
          description: A list of products currently in the wishlist.
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Product'
              examples:
                successfulWishlistWithProducts:
                  summary: Example wishlist with 3 products
                  value:
                    - productId: "PROD001"
                      name: "Ergonomic Mechanical Keyboard"
                      price: 189.99
                      currency: "USD"
                    - productId: "PROD002"
                      name: "Noise-Cancelling Headphones"
                      price: 299.00
                      currency: "USD"
                    - productId: "PROD003"
                      name: "Ultra-Wide Gaming Monitor"
                      price: 549.50
                      currency: "USD"
        '500':
          description: Internal Server Error.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
    post:
      summary: Add a product to the wishlist
      description: |
        Adds a specified product to the user's wishlist.
        This operation is neither safe nor idempotent, as per RFC 9110.
        A 201 Created response includes a Location header pointing to the newly created resource.
      operationId: addProductToWishlist
      tags:
        - Wishlist
      requestBody:
        description: Product ID to add to the wishlist.
        required: true
        content:
          application/json:
            schema:
              type: object
              required:
                - productId
              properties:
                productId:
                  type: string
                  description: The unique identifier of the product to add.
                  example: "PROD004"
      responses:
        '201':
          description: Product successfully added to the wishlist.
          headers:
            Location:
              description: The URI of the newly added wishlist item resource.
              schema:
                type: string
                example: "/wishlist/PROD004"
        '400':
          description: Bad Request (e.g., missing product ID, invalid format, product already exists).
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
              examples:
                productAlreadyExists:
                  summary: Product already in wishlist
                  value:
                    code: "WISHLIST_001"
                    message: "Product 'PROD004' is already in the wishlist."
                invalidProductId:
                  summary: Invalid product ID format
                  value:
                    code: "VALIDATION_001"
                    message: "Invalid productId format. Must be a non-empty string."
        '404':
          description: Product not found (i.e., the product ID provided does not correspond to an existing product in the catalog).
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
              examples:
                productCatalogNotFound:
                  summary: Product not found in catalog
                  value:
                    code: "PRODUCT_001"
                    message: "Product 'PROD004' not found in the product catalog."
        '500':
          description: Internal Server Error.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

  /wishlist/{productId}:
    delete:
      summary: Remove a product from the wishlist
      description: |
        Removes a specific product from the user's wishlist.
        This operation is idempotent (multiple identical requests have the same effect as a single one),
        but not safe (it changes the server's state), as per RFC 9110.
      operationId: removeProductFromWishlist
      tags:
        - Wishlist
      parameters:
        - name: productId
          in: path
          description: The unique identifier of the product to remove from the wishlist.
          required: true
          schema:
            type: string
            example: "PROD001"
      responses:
        '204':
          description: Product successfully removed from the wishlist. No Content.
        '404':
          description: Product not found in the wishlist.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
              examples:
                productNotInWishlist:
                  summary: Product not in wishlist
                  value:
                    code: "WISHLIST_002"
                    message: "Product 'PROD005' not found in wishlist."
        '500':
          description: Internal Server Error.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

components:
  schemas:
    Product:
      type: object
      description: Represents a product in the wishlist.
      required:
        - productId
        - name
        - price
        - currency
      properties:
        productId:
          type: string
          description: Unique identifier for the product.
          example: "PROD001"
        name:
          type: string
          description: Name of the product.
          example: "Ergonomic Mechanical Keyboard"
        price:
          type: number
          format: float
          description: Price of the product.
          example: 189.99
        currency:
          type: string
          description: Currency of the product price (e.g., USD, EUR).
          example: "USD"
    Error:
      type: object
      description: Standard error response format compliant with RFC 9110 problem details principles.
      required:
        - code
        - message
      properties:
        code:
          type: string
          description: A unique, application-specific error code.
          example: "GENERIC_001"
        message:
          type: string
          description: A human-readable explanation specific to this occurrence of the problem.
          example: "An unexpected error occurred while processing your request."

Gemini:
Hello! I'm ready to act as a REST API for your Wishlist. Please send your HTTP requests, and I'll respond based on the OpenAPI specification provided.

User:
GET https://api.example.com/v1/wishlist

Gemini:
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "productId": "PROD001",
    "name": "Ergonomic Mechanical Keyboard",
    "price": 189.99,
    "currency": "USD"
  },
  {
    "productId": "PROD002",
    "name": "Noise-Cancelling Headphones",
    "price": 299.00,
    "currency": "USD"
  },
  {
    "productId": "PROD003",
    "name": "Ultra-Wide Gaming Monitor",
    "price": 549.50,
    "currency": "USD"
  }
]

User:
POST https://api.example.com/wishlist

{
  "productId": "PROD005"
}

Gemini:
HTTP/1.1 201 Created
Location: /wishlist/PROD005
Content-Length: 0

User:
GET https://api.example.com/v1/wishlist

Gemini:
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "productId": "PROD001",
    "name": "Ergonomic Mechanical Keyboard",
    "price": 189.99,
    "currency": "USD"
  },
  {
    "productId": "PROD002",
    "name": "Noise-Cancelling Headphones",
    "price": 299.00,
    "currency": "USD"
  },
  {
    "productId": "PROD003",
    "name": "Ultra-Wide Gaming Monitor",
    "price": 549.50,
    "currency": "USD"
  },
  {
    "productId": "PROD005",
    "name": "Wireless Charging Pad",
    "price": 45.00,
    "currency": "USD"
  }
]

User:
DELETE https://api.example.com/v1/wishlist/PROD003

Gemini:
HTTP/1.1 204 No Content

User:
GET https://api.example.com/v1/wishlist

Gemini:
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "productId": "PROD001",
    "name": "Ergonomic Mechanical Keyboard",
    "price": 189.99,
    "currency": "USD"
  },
  {
    "productId": "PROD002",
    "name": "Noise-Cancelling Headphones",
    "price": 299.00,
    "currency": "USD"
  },
  {
    "productId": "PROD005",
    "name": "Wireless Charging Pad",
    "price": 45.00,
    "currency": "USD"
  }
]

User:
DELETE https://api.example.com/v1/wishlist/PROD003

Gemini:
HTTP/1.1 404 Not Found
Content-Type: application/json

{
  "code": "WISHLIST_002",
  "message": "Product 'PROD003' not found in wishlist."
}

User:
POST https://api.example.com/wishlist

{
  "someparam": "PROD009"
}

Gemini:
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "code": "VALIDATION_001",
  "message": "Invalid productId format. Must be a non-empty string."
}
```

## Prompts

* The following describes the API Simulator prompt pattern. It has 5 main sections: (1) Intent and Context, (2) Motivation, (3) Structure and Key Ideas, (4) Example Implementation, and (5) Consequences. Summarise it in bullet points form, section by section. [Text of the pattern]

## Source

* White, J., Hays, S., Fu, Q., Spencer-Smith, J., & Schmidt, D. C. (2023). _ChatGPT Prompt Patterns for Improving Code Quality, Refactoring, Requirements Elicitation, and Software Design._ ArXiv.org. <https://arxiv.org/abs/2303.07839>
