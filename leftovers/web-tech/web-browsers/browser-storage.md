# Browser storage

## Types

![](../../../aaa-assets/browser-storage-1.png)

### console examples

```javascript
// add item to local storage
localStorage.setItem('key', 'val')
// get/remove item from local storage
console.log(localStorage.getItem('key')
console.log(localStorage.removeItem('key')

// session storage, other examples are the same
sessionStorage.setItem('key', 'val')

// cookies
document.cookie = 'key=val'

// example with all parameters
document.cookie = "name=value; expires=Wed, 21 Oct 2025 07:28:00 GMT; path=/; domain=example.com; secure; samesite=Strict";
```

### Cookies

links
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies

A cookie with:
- `Secure` attribute is only sent over the HTTPS protocol
- `HttpOnly` attribute is inaccessible to the JavaScript [`Document.cookie`](https://developer.mozilla.org/en-US/docs/Web/API/Document/cookie) API; it's only sent to the server. For example, cookies that persist in server-side sessions don't need to be available to JavaScript and should have the `HttpOnly` attribute. This precaution helps mitigate cross-site scripting ([XSS](https://developer.mozilla.org/en-US/docs/Web/Security/Types\_of\_attacks#cross-site\_scripting\_\(xss\))) attacks.
- the domain attribute `.domain.com`, it is accessible by all subdomains of `domain.com. A` cookie set on `example.com` without specifying the domain attribute would only be accessible on `example.com` and not on `subdomain.example.com`

`SameSite` attribute controls the sending of cookies on cross-site requests, providing protection against CSRF attacks. 
It can have three values: 
- `Strict` sends cookies only from the origin site
- `Lax` sends them from the origin site and when the user navigates to it
- `None` allows cookies on both types of requests but only in secure contexts when the Secure attribute is set. 
If no `SameSite` attribute is set, the cookie is treated as Lax.
