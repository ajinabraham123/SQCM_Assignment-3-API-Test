# SQCM Assignment 3

This document provides a detailed explanation of the API testing practices completed using Postman. Each step is documented with corresponding screenshots, explaining their purpose and results.

## Table of Contents
1. [Introduction](#introduction)
2. [Practice 1: API Basics](#practice-1-api-basics)
3. [Practice 2: Order Creation API](#practice-2-order-creation-api)
4. [Practice 3: Tool Retrieval API](#practice-3-tool-retrieval-api)
5. [Conclusion](#conclusion)

---

## Introduction

This assignment focuses on testing RESTful APIs using Postman. Each practice contains detailed steps, validation scripts, and results to ensure API correctness and proper functionality.

---

## Practice 1: API Basics

### Objective
- Test the `GET` endpoint for retrieving tools by category.
- Validate that all tools in the response belong to the specified category (`electric-generators`).

### Steps and Screenshots
1. **Sending a GET Request**  
   - A `GET` request is sent to `https://simple-tool-rental-api.glitch.me/tools?category=electric-generators`.  
   - **Screenshot**: `Screenshot 2024-11-24 at 4.45.03 PM.png`  
     This screenshot shows the request being made with the query parameter `category=electric-generators`. The response displays a list of tools in JSON format.

2. **Validation Script**  
   - A script validates that every tool in the response belongs to the `electric-generators` category.  
   - **Screenshot**: `Screenshot 2024-11-24 at 4.47.18 PM.png`  
     The screenshot highlights the validation script, which iterates over the response data to check the `category` property of each tool.

3. **Test Result: Passing the Validation**  
   - The test confirms that all tools belong to the correct category.  
   - **Screenshot**: `Screenshot 2024-11-24 at 4.48.00 PM.png`  
     This shows the test result as "PASS," confirming that all tools were successfully validated.

4. **Intentional Failure**  
   - The script is modified to check for the incorrect category (`solar-panels`) to demonstrate a failure.  
   - **Screenshot**: `Screenshot 2024-11-24 at 4.50.32 PM.png`  
     The test result "FAIL" indicates a mismatch between the expected and actual category.

---

## Practice 2: Order Creation API

### Objective
- Test the `POST` endpoint for creating orders.
- Validate that the response contains:
  1. A `created` flag set to `true`.
  2. A valid `orderId`.

### Steps and Screenshots
1. **Order Creation Request**  
   - A `POST` request is sent to `https://simple-tool-rental-api.glitch.me/orders` with the following body:
     ```json
     {
         "toolId": "{{toolId}}",
         "customerName": "John Doe"
     }
     ```
   - **Screenshot**: `Screenshot 2024-11-26 at 3.03.52 PM.png`  
     This screenshot shows the API request setup and response with a status code `201 Created`.

2. **Validation Script for `created` and `orderId`**  
   - The script validates:
     - The presence of the `created` flag, ensuring it is `true`.
     - The presence of an `orderId`, ensuring it is a non-empty string.  
   - **Screenshot**: `Screenshot 2024-11-26 at 3.55.06 PM.png`  
     This screenshot shows the script used for validation.

3. **Test Result: Passing the Validation**  
   - The test confirms both validations pass.  
   - **Screenshot**: `Screenshot 2024-11-26 at 3.55.51 PM.png`  
     The "PASS" result indicates successful validation of both the `created` flag and `orderId`.

---

## Practice 3: Tool Retrieval API

### Objective
- Test the `GET` endpoint for retrieving a tool by ID.
- Validate:
  1. The `toolId` in the response matches the requested ID.
  2. The `current-stock` is greater than `0`.

### Steps and Screenshots
1. **Tool Retrieval Request**  
   - A `GET` request is sent to `https://simple-tool-rental-api.glitch.me/tools/{{toolId}}`.  
   - **Screenshot**: `Screenshot 2024-11-26 at 4.09.48 PM.png`  
     This screenshot shows the request setup with the tool ID and the JSON response.

2. **Validation Script for `toolId`**  
   - A script verifies that the `toolId` in the response matches the `toolId` from the request.  
   - **Screenshot**: `Screenshot 2024-11-26 at 4.09.59 PM.png`  
     This screenshot shows the script that extracts the `toolId` from the request URL and compares it with the response.

3. **Validation Script for `current-stock`**  
   - A script ensures the `current-stock` exists and is greater than `0`.  
   - **Screenshot**: `Screenshot 2024-11-26 at 4.10.52 PM.png`  
     This screenshot highlights the script checking the `current-stock` value.

4. **Combined Test Results**  
   - Both validations (`toolId` and `current-stock`) pass.  
   - **Screenshot**: `Screenshot 2024-11-26 at 4.11.33 PM.png`  
     This screenshot shows both tests passing successfully.

---

## Conclusion

This assignment demonstrates:
1. Effective use of Postman to test and validate RESTful APIs.
2. Writing robust validation scripts to ensure API responses meet requirements.
3. Documenting the testing process with screenshots for clarity.

Each step is linked to the corresponding screenshots to ensure a seamless grading process. If further clarification is required, refer to the referenced screenshots.
