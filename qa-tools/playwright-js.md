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

```javascript
const { test, expect } = require('@playwright/test');
test('check load of main page', async ({ page }) => {
  await page.goto('https://google.com/');
  // Expect a title "to contain" a substring.
  await expect(page).toHaveTitle(/Google/);
});
```

### run

```bash
npx playwright test
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
