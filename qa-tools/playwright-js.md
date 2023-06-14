# Playwright - JS

## Links

FAQ - [https://applitools.com/blog/top-playwright-questions-answered](https://applitools.com/blog/top-playwright-questions-answered/)

Tutor - [https://testautomationu.applitools.com/js-playwright-tutorial](https://testautomationu.applitools.com/js-playwright-tutorial)

Webinar - [https://applitools.com/event/playwright-a-new-test-automation-framework-for-the-modern-web](https://applitools.com/event/playwright-a-new-test-automation-framework-for-the-modern-web/)

## Installation

#### Requirements&#x20;

node.js+npm

```bash
# Run from your project's root directory
npm init playwright@latest
# Or create a new project
npm init playwright new-project

# Or install manualy 
npm i -D @playwright/test
# install supported browsers
npx playwright install
```

notes

```bash
Inside that directory, you can run several commands:

  npx playwright test
    Runs the end-to-end tests.

  npx playwright test --project=chromium
    Runs the tests only on Desktop Chrome.

  npx playwright test tests/example.spec.ts
    Runs the tests of a specific file.

  npx playwright test --debug
    Runs the tests in debug mode.

We suggest that you begin by typing:

  cd new-project
  npx playwright test

And check out the following files:
  - ./new-project/tests/example.spec.ts - Example end-to-end test
  - ./new-project/playwright.config.ts - Playwright Test configuration

Visit https://playwright.dev/docs/intro for more information. ✨

Happy hacking
```

### create

test-file should contain '.spec' in name

`example.test.spec.js` - example

`tests/example.test.spec.ts` - path

```javascript
const { test, expect } = require('@playwright/test');

test('check load of main page', async ({ page }) => {
  await page.goto('https://google.com/');
  await expect(page).toHaveTitle(/Google/); // Expect a title "contain" a substring
});
```

### run

```bash
# run all
npx playwright test

# run one
npx playwright test tests/example.test.spec.ts
```

## code snippets

`.type .goto page.$`

```javascript
const { chromium } = require('playwright');
// https://playwright.dev/docs/api/class-elementhandle#element-handle-type

( async () => {
    // function code
    // launching browser
    const browser = await chromium.launch({ headless: false, slowMo: 100});
    const page = await browser.newPage();
    await page.goto('https://the-internet.herokuapp.com/forgot_password');
    // code to type in email textbox
    const email = await page.$('#email');
    // delaying typing 50 ms to simulate real user speed typing
    await email.type('ixchel@mail.com', { delay : 50});
    await page.click('#smthg');
    await browser.close();
})();
```

### test

`test.describe` is a method that declares a group of tests. \
It takes two arguments: a string that represents the title of the group, and the second argument is a callback function that contains all the tests belonging to this group. When `test.describe` is called, it immediately runs the callback function and any tests added in this callback will belong to this group.

`test`

takes two arguments: a string representing the title of the test, and an async function that defines the test itself. The async function receives an object with fixtures and optional TestInfo as its argument.

`expect`

To make an assertion, call `expect(value)` and choose a matcher that reflects the expectation. There are many generic matchers like `toEqual`, `toContain`, and `toBeTruthy` that can be used to assert any conditions.\
[https://playwright.dev/docs/test-assertions](https://playwright.dev/docs/test-assertions)

```javascript
test.describe('Pay button appearance', () => { // declare group of tests
  test('Pay button is displaying if Pay Enabled', async ({ // declare test name
    page, // recieve page object
    request, // recieve request object
  }) => {
    const PayWidget = new PayWidgetComponent(page); // get page elements for test

    await openPayPage(page, request, token, { // open page with test data
      Id: TestId,
    });
    
    await expect( // assertion function
      PayWidget.PayButton, // component
      "I don't see the Pay button" // custom expect message
    ).toBeVisible(); // matcher for assertion 
    await expect(
      PayWidget.ButtonSpmPreview,
      'I can see Pay SPM preview on button'
    ).toBeHidden();
  });
```
