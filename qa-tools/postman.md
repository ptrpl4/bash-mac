# Postman

### Variables Types

```javascript
pm.globals.set("variable_key", "variable_value");
pm.collectionVariables.set("variable_key", "variable_value");
pm.environment.set("variable_key", "variable_value");
```

### Snippets

<pre class="language-javascript"><code class="lang-javascript"><strong>// JSON value check
</strong><strong>pm.test("Your test name", function () {
</strong>    var jsonData = pm.response.json();
    pm.expect(jsonData.value).to.eql(100);
});
// check body is not null
pm.test("Check that response body is not null", ()=>{
   pm.response.to.be.have.body
    })
// setting variable from JSON response Body
var jsonData = pm.response.json();
pm.environment.set("newToken", jsonData.headers['postman-token']);
</code></pre>
