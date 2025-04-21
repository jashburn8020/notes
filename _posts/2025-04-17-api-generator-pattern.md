---
layout: post
title: API Generator Pattern
categories: ai llm pattern software
published: true
plantuml: false
---

The API Generator Pattern, a prompt pattern to review specifications provided to a developer or development team.

This summary is mostly generated using Google Gemini from an academic paper (see Source below). The example at the end is from an actual interaction with Google Gemini (2.0 Flash).

## API Generator Pattern

Here's a summary of the API Generator Pattern in bullet points, section by section:

### Intent and Context

* Generates API specifications (e.g., REST API) from natural language requirements or system descriptions.
* Goal is to rapidly explore API designs, formalise design early, and provide a starting point for manual refinement.

### Motivation

* Manual API specification design is often time-consuming.
* Significant manual effort can lead to:
  * Fewer design options explored.
  * Delayed systematic API specifications.
  * Code being the sole source of truth for integration.
* Key motivation is to reduce/eliminate API creation cost, enabling earlier creation and careful design consideration.

### Structure and Key Ideas

Fundamental contextual statements:

1. Using system description X.
2. Generate an API specification for the system.
3. The API specification should be in format Y.

### Example Implementation

* Example prompt for generating an OpenAPI specification:
  * "Generate an OpenAPI specification for a web application that would implement the listed requirements."
* Uses OpenAPI as a concrete specification format.
* Assumes prior discussion or textual description of requirements.
* More detailed requirements lead to more accurate generated APIs.
* Can be used for thought experiments with simpler prompts, e.g.,
  * "Generate an OpenAPI specification for a web application related to cooking."

### Consequences

* Provides developers with a powerful tool to experiment with different API designs from descriptions or requirements.
* Enables rapid creation and comparison of multiple potential API designs before final selection.
* Addresses the tedium of manual API writing, encouraging exploration of more options.
* Incentivises earlier API specification creation by automating the process.
* Complements existing (non-LLM) code-to-API tools by not requiring initial code.
* Can be combined with code generation from API specifications to accelerate implementation.
* Integrates well with the API Simulator pattern for evaluation and the Data-Guided Refactoring pattern for refinement.

### Example

```text
User:
Generate an OpenAPI specification for a web application with a REST API that would implement the requirements below:

- As a registered user, I want to click a clearly visible "Add to Wishlist" button on a product page so that I can save items I'm interested in for later consideration without immediately adding them to my cart.
- As a guest user, I want to click a clearly visible "Add to Wishlist" button on a product page so that I can save items I'm interested in, and I should be prompted to register or log in so that I can access my saved items later.
- As a user, I want to see a confirmation message or visual cue after clicking "Add to Wishlist" so that I know the action was successful.
- As a user, I want the "Add to Wishlist" button to clearly indicate whether the item is already in my wishlist so that I don't accidentally add the same item multiple times.
- As a user, when an item is already in my wishlist, I want the "Add to Wishlist" button to change to a "View Wishlist" or "Remove from Wishlist" option so that I can easily manage my saved items directly from the product page.
- As a user, I want the wishlist functionality to persist across different browsing sessions so that I can access my saved items even if I close my browser and return later (as a logged-in user).
- As a user, I want the "Add to Wishlist" button to be located near the product image and key product information so that it is easy to find and use.
- As a user, I want the website to handle cases where a product added to my wishlist becomes unavailable and notify me in my wishlist so that I am aware of the change in availability.
- As a registered user, if the system encounters an error while trying to add a product to my wishlist, I want to see a clear and informative error message (e.g., "There was an error adding this item to your wishlist. Please try again later.") so that I am aware that the action failed and understand what to do next.
- As a guest user, if the system encounters an error while trying to add a product to my wishlist, I want to see a clear and informative error message (e.g., "There was an error saving this item to your temporary wishlist. Please try again later.") so that I am aware that the action failed and understand what to do next.

Gemini:
openapi: 3.0.0
info:
  title: Wishlist API
  version: v1
  description: API for managing user wishlists in an e-commerce application.

servers:
  - url: http://localhost:8080/api # Replace with your actual API base URL

components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT

  schemas:
    ProductId:
      type: integer
      description: Unique identifier for a product.
      example: 123

    UserId:
      type: integer
      description: Unique identifier for a registered user.
      example: 456

    WishlistItemResponse:
      type: object
      properties:
        productId:
          $ref: '#/components/schemas/ProductId'
        addedAt:
          type: string
          format: date-time
          description: Timestamp when the item was added to the wishlist.
          example: '2025-04-17T00:50:00Z'
        isAvailable:
          type: boolean
          description: Indicates if the product is currently available.
          example: true
        availabilityMessage:
          type: string
          nullable: true
          description: Message indicating the availability status (e.g., "Out of Stock", "Backordered").
          example: 'Out of Stock'

    WishlistResponse:
      type: array
      items:
        $ref: '#/components/schemas/WishlistItemResponse'

    ErrorResponse:
      type: object
      properties:
        message:
          type: string
          description: A human-readable error message.
          example: 'There was an error adding this item to your wishlist. Please try again later.'

paths:
  /wishlist:
    get:
      summary: Get the current user's wishlist.
      description: >-
        Retrieves the wishlist for the authenticated user. Requires user authentication.
      security:
        - bearerAuth: []
      responses:
        '200':
          description: Successful retrieval of the wishlist.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/WishlistResponse'
        '401':
          description: Unauthorized - User not authenticated.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Authentication required.'
        '500':
          description: Internal server error.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'An unexpected error occurred on the server.'

    post:
      summary: Add a product to the user's wishlist.
      description: >-
        Adds a specified product to the authenticated user's wishlist. Requires user authentication.
      security:
        - bearerAuth: []
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                productId:
                  $ref: '#/components/schemas/ProductId'
              required:
                - productId
            example:
              productId: 789
      responses:
        '201':
          description: Product successfully added to the wishlist.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/WishlistItemResponse'
        '400':
          description: Invalid request payload (e.g., missing productId).
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Missing or invalid productId in the request.'
        '401':
          description: Unauthorized - User not authenticated.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Authentication required.'
        '409':
          description: Product already exists in the user's wishlist.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Product is already in your wishlist.'
        '500':
          description: Internal server error.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'There was an error adding this item to your wishlist. Please try again later.'

  /wishlist/{productId}:
    delete:
      summary: Remove a product from the user's wishlist.
      description: >-
        Removes a specified product from the authenticated user's wishlist. Requires user authentication.
      security:
        - bearerAuth: []
      parameters:
        - in: path
          name: productId
          required: true
          schema:
            $ref: '#/components/schemas/ProductId'
          description: The ID of the product to remove from the wishlist.
      responses:
        '204':
          description: Product successfully removed from the wishlist.
        '401':
          description: Unauthorized - User not authenticated.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Authentication required.'
        '404':
          description: Product not found in the user's wishlist.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Product not found in your wishlist.'
        '500':
          description: Internal server error.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'There was an error removing this item from your wishlist. Please try again later.'

  /guest/wishlist:
    post:
      summary: Add a product to the guest user's temporary wishlist.
      description: >-
        Adds a specified product to a temporary wishlist for a guest user.
        This wishlist is typically stored in a browser cookie or local storage.
        The response will include a temporary identifier (if applicable) for the guest wishlist.
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                productId:
                  $ref: '#/components/schemas/ProductId'
              required:
                - productId
            example:
              productId: 101
      responses:
        '200':
          description: Product successfully added to the temporary wishlist.
          content:
            application/json:
              schema:
                type: object
                properties:
                  productId:
                    $ref: '#/components/schemas/ProductId'
                  message:
                    type: string
                    example: 'Product added to your temporary wishlist. Please register or log in to save it permanently.'
        '400':
          description: Invalid request payload (e.g., missing productId).
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Missing or invalid productId in the request.'
        '409':
          description: Product already exists in the guest user's temporary wishlist.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Product is already in your temporary wishlist.'
        '500':
          description: Internal server error.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'There was an error saving this item to your temporary wishlist. Please try again later.'

    delete:
      summary: Remove a product from the guest user's temporary wishlist.
      description: >-
        Removes a specified product from the guest user's temporary wishlist.
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                productId:
                  $ref: '#/components/schemas/ProductId'
              required:
                - productId
            example:
              productId: 101
      responses:
        '204':
          description: Product successfully removed from the temporary wishlist.
        '400':
          description: Invalid request payload (e.g., missing productId).
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Missing or invalid productId in the request.'
        '404':
          description: Product not found in the guest user's temporary wishlist.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'Product not found in your temporary wishlist.'
        '500':
          description: Internal server error.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example:
                message: 'There was an error removing this item from your temporary wishlist. Please try again later.'
```

* Note the design choice with the `/guest/wishlist` path.
* Note also errors such as the request body for `DELETE /guest/wishlist`.

## Prompts

* The following describes the API Generator Pattern. It has 5 main sections: (1) Intent and Context, (2) Motivation, (3) Structure and Key Ideas, (4) Example Implementation, and (5) Consequences. Please summarise it in bullet points form, section by section. [Text of the pattern]

## Source

* White, J., Hays, S., Fu, Q., Spencer-Smith, J., & Schmidt, D. C. (2023). _ChatGPT Prompt Patterns for Improving Code Quality, Refactoring, Requirements Elicitation, and Software Design._ ArXiv.org. <https://arxiv.org/abs/2303.07839>
