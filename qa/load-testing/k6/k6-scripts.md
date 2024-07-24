# k6 scripts

#### links

official examples - [https://k6.io/docs/examples](https://k6.io/docs/examples)

```javascript
// Single request
import http from "k6/http";

export const options = {
  iterations: 1,
};

export default function () {
  const response = http.get("https://test-api.k6.io/public/crocodiles/");
}
```
