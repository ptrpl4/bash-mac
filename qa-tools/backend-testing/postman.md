# Postman

### Variables Types

```javascript
pm.globals.set("variable_key", "variable_value");
pm.collectionVariables.set("variable_key", "variable_value");
pm.environment.set("variable_key", "variable_value");
```

### Snippets

```javascript
// JSON value check
pm.test('Your test name', () => {
  const jsonData = pm.response.json()
  pm.expect(jsonData.value).to.eql(100)
})

// body is not null check
pm.test('Check that response body is not null', () => {
  pm.response.to.be.have.body
})

// get variable from JSON response
const jsonData = pm.response.json()
pm.environment.set('newToken', jsonData.headers['postman-token'])

// status 200 check
pm.test('Status code is 200', () => {
  pm.response.to.have.status(200)
})

```
