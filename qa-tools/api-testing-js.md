---
description: Generic info about JS API test tools and frameworks
---

# API Testing - JS

## Most Common Tools

### SuperTest

[https://github.com/ladjs/supertest](https://github.com/ladjs/supertest)\
Library for API request

### Mocha

[https://mochajs.org/](https://mochajs.org/)

Framework for JS test management

### Chai

[https://www.chaijs.com/](https://www.chaijs.com/)

Assertion library

## Using SuperTest+Mocha+Chai

example test

<pre class="language-javascript"><code class="lang-javascript">const { describe, it } = require('mocha');
const request = require('supertest');

const testData = {

<strong>describe('GET /cards', function(){
</strong>    it('get user cards', function(done) {
        request('https://wallet.site.com')
        .get('/api/v1/cards')
        .set('authorization', 'Bearer token')
        .expect(200, done);
    })
})
</code></pre>
