# PostMan

## Setting variable from JSON response Body

```javascript
var jsonData = pm.response.json();
pm.environment.set("newToken", jsonData.headers['postman-token']);
```

### Varibles Types

```
pm.globals.set("variable_key", "variable_value");
```

```
pm.collectionVariables.set("variable_key", "variable_value");
```

```
pm.environment.set("variable_key", "variable_value");
```

### JSON value check

```javascript
pm.test("Your test name", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.value).to.eql(100);
});
```
