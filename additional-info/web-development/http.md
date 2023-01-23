---
description: Hypertext Transfer Protocol
---

# 🔧 HTTP

![pic by hyperskill](<../../.gitbook/assets/image (18) (1).png>)

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

## HTTP Request Methods

### **Options**

The **HTTP `OPTIONS` method** requests permitted communication options for a given URL or server. A client can specify a URL with this method, or an asterisk (`*`) to refer to the entire server.

#### [Preflighted requests in CORS](https://developer.mozilla.org/en-US/docs/Glossary/XHR\_\(XMLHttpRequest\)#preflighted\_requests\_in\_cors) <a href="#preflighted_requests_in_cors" id="preflighted_requests_in_cors"></a>

In [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS), a [preflight request](https://developer.mozilla.org/en-US/docs/Glossary/Preflight\_request) is sent with the `OPTIONS` method so that the server can respond if it is acceptable to send the request.&#x20;

example

```
OPTIONS /resources/post-here/ HTTP/1.1
Host: bar.example
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
Origin: https://foo.example
Access-Control-Request-Method: POST
Access-Control-Request-Headers: Content-Type
```

The server now can respond if it will accept a request under these circumstances. In this example, the server response says that:

[`Access-Control-Allow-Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin)

The `https://foo.example` origin is permitted to request the `bar.example/resources/post-here/` URL via the following:

[`Access-Control-Allow-Methods`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Methods)

[`POST`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST), [`GET`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/GET), and `OPTIONS` are permitted methods for the URL. (This header is similar to the [`Allow`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Allow)response header, but used only for [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS).)

[`Access-Control-Allow-Headers`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Headers)

Any script inspecting the response is permitted to read the values of the `X-PINGOTHER` and `Content-Type` headers.

[`Access-Control-Max-Age`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Max-Age)

The above permissions may be cached for 86,400 seconds (1 day).

```
HTTP/1.1 204 No Content
Date: Mon, 01 Dec 2008 01:15:39 GMT
Server: Apache/2.0.61 (Unix)
Access-Control-Allow-Origin: https://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: 86400
Vary: Accept-Encoding, Origin
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
```





## Links

Methods - [https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
