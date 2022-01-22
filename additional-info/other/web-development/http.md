---
description: Hypertext Transfer Protocol
---

# 🔧 HTTP

![pic by hyperskill](<../../../.gitbook/assets/image (18).png>)

## Basics

In the HTTP protocol, all messages consist of text strings. Both requests and responses have roughly the same standardized format:

1. **Start line** which may vary:
   * for requests, it indicates the type of request (**method**) and the URL where to send it (**target**);
   * for responses, it contains a status code to determine the success of the operation.
2. **Headers** which describe the message and convey various parameters.
3. **Body** in which the message data is located.

The **start line** and the **header** are required attributes, so the other parts may be empty.

## **Status codes**

| **1xx: Informational** | Codes beginning with "1" are called information codes. They report on how client requests are processed.             |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **2xx: Success**       | Messages of this class inform that the action requested by the client has been successfully accepted for processing. |
| **3xx: Redirection**   | It means further action must be taken in order to complete the request.                                              |
| **4xx: Client Error**  | It reports errors on the client's side.                                                                              |
| **5xx: Server Error**  | The code indicates that the operation was unsuccessful due to the fault of the server.                               |

****

## Links

Methods - [https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
