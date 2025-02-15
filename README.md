# StarUML-Sequence-Diagram
Sequence Diagram implemented in StarUML for Email System.

## Overview
This sequence diagram for an email system which includes actors, use cases, relationships, syntax explanation, access specifiers, and feature function details. The sequence diagram represents the interaction between the Handler, User, and Authenticator during email-related operations such as fetching, verifying, updating, and sending/receiving emails.

## Actors
- **Handler**: Manages email operations such as fetching, modifying, and sending/receiving emails.
- **User**: Interacts with the system by providing login credentials, email information, and modification requests.
- **Authenticator**: Verifies login credentials for secure access and handles email verification or updates.

## Use Cases
- **Fetch Email Information**
- **Authenticate User Login**
- **Modify Email Details**
- **Send or Receive Email**

## Relationships
- The Handler interacts with both the User and the Authenticator to manage email-related operations.
- The User provides email details and credentials for authentication.
- The Authenticator validates credentials, verifies user identity, and updates email information as needed.

## Syntax Explanation
- **Actors**: Represented as rectangles at the top of vertical dashed lines (lifelines).
- **Messages**:
  - Solid arrows represent synchronous calls (e.g., `sendRequestForEmail()`).
  - Dashed arrows represent responses (e.g., `getEmail()`).
- **Activation Bars**: Thin rectangles on lifelines indicate when an actor is actively performing an operation.

## Access Specifiers
- **Public (`+`)**: Functions like `sendRequestForEmail()` and `sendOrReceiveEmail()` are accessible across all components.
- **Private (`-`)**: Internal functions like `checkAndUpdateEmail()` are restricted to specific components (e.g., Authenticator).
- **Protected (`#`)**: Intermediate functions like `sendRequestToModifyInfo()` are accessible only within related components (Handler and Authenticator).

## Feature Functions
| Use Case               | Function                                | Description                                     | Access Specifier |
|------------------------|----------------------------------------|-------------------------------------------------|------------------|
| Fetch Email Information | `sendRequestForEmail()`               | Sends a request to retrieve user email         | Public (`+`)     |
| Authenticate User Login | `validateCredentials(username, password)` | Validates user login credentials             | Private (`-`)    |
| Modify Email Details   | `sendRequestToModifyInfo(userID)`     | Sends a request to update user email details   | Protected (`#`)  |
| Update Email           | `checkAndUpdateEmail(userID, newEmail)` | Updates email after validation               | Private (`-`)    |
| Send or Receive Email  | `sendOrReceiveEmail(senderID, receiverID)` | Sends or receives emails after verification | Public (`+`)     |

## Steps in the Workflow
1. The Handler sends a request to fetch the User's email information (`sendRequestForEmail()`).
2. The User responds with their email details (`getEmail()`).
3. The User enters login credentials for authentication (`validateCredentials()`).
4. The Authenticator verifies the credentials and allows further actions (`verifyAndAllowUser()`).
5. If required, the Handler sends a request to modify or update the User's email information (`sendRequestToModifyInfo()`).
6. The Authenticator processes this request and updates the email details securely (`checkAndUpdateEmail()`).
7. After successful verification, the Handler sends a request to perform email-related actions like sending or receiving emails (`sendOrReceiveEmail()`).
8. The Authenticator grants permission for these actions based on successful validation.

## Conclusion
This sequence diagram outlines how users interact with an email system while ensuring secure access through authentication and efficient functionality via handlers and authenticators. By following this workflow, developers can implement a robust backend system for managing user emails securely.
