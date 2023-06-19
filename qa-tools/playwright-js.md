# Playwright - JS

#### Links

FAQ - [https://applitools.com/blog/top-playwright-questions-answered](https://applitools.com/blog/top-playwright-questions-answered/)\
Tutor - [https://testautomationu.applitools.com/js-playwright-tutorial](https://testautomationu.applitools.com/js-playwright-tutorial)\
Webinar - [https://applitools.com/event/playwright-a-new-test-automation-framework-for-the-modern-web](https://applitools.com/event/playwright-a-new-test-automation-framework-for-the-modern-web/)

## Basics

#### quick init

```bash
# you need node.js (npm)
# Run from your project's root directory
npm init playwright@latest

# Or create a new project
npm init playwright new-project

# Or install manualy 
npm i -D @playwright/test

# install supported browsers
npx playwright install
```

#### File structure

`./tests/example.spec.ts` - Example end-to-end test\
`./playwright.config.ts` - Playwright Test configuration

```javascript
// example test
const { test, expect } = require('@playwright/test');

test('check load of main page', async ({ page }) => {
  await page.goto('https://google.com/');
  await expect(page).toHaveTitle(/Google/); // Expect a title "contain" a substring
});
```

### playwright runner

```bash
# run all
npx playwright test

# run one
npx playwright test tests/example.test.spec.ts

# Runs the tests only on Desktop Chrome.
npx playwright test --project=chromium

# Runs the tests in debug mode.
npx playwright test --debug
```

### playwright config

`playwright.config.ts`

docs - https://playwright.dev/docs/test-configuration

config example - [https://github.com/raptatinha/tau-introduction-to-playwright/blob/chapter-2/playwright.config.ts](https://github.com/raptatinha/tau-introduction-to-playwright/blob/chapter-2/playwright.config.ts)

```javascript
import { defineConfig, devices } from '@playwright/test';
import baseEnvUrl from './utils/environmentBaseUrl';

require('dotenv').config();

export default defineConfig({
  testDir: './tests',

  fullyParallel: true, // Run tests in files in parallel

  // Fail the build on CI if you accidentally left test.only in the source code
  forbidOnly: !!process.env.CI,

  /* Retry on CI only */
  // retries: process.env.CI ? 2 : 0,
  retries: 2,

  /* Opt out of parallel tests on CI. */
  workers: process.env.CI ? 1 : undefined,

  /* Reporter to use. See https://playwright.dev/docs/test-reporters */
  reporter: 'html',
  // reporter: [['html', { open: 'always' }]], //always, never and on-failure (default).
  // reporter: [['html', { outputFolder: 'my-report' }]], // report is written into the playwright-report folder in the current working directory. override it using the PLAYWRIGHT_HTML_REPORT
  // reporter: 'dot',
  // reporter: 'list',
  /**
    reporter: [
      ['list'],
      ['json', {  outputFile: 'test-results.json' }]
    ],
  */
  /**
   * custom reports: https://playwright.dev/docs/test-reporters#custom-reporters 
  */
  
  /* Shared settings for all the projects below. See https://playwright.dev/docs/api/class-testoptions. */
  use: {
    /* Base URL to use in actions like `await page.goto('/')`. */
    // baseURL: 'http://127.0.0.1:3000',

    /* Collect trace when retrying the failed test. See https://playwright.dev/docs/trace-viewer */
    trace: 'on-first-retry',
    screenshot: 'only-on-failure',
    // headless: false,
    // ignoreHTTPSErrors: true,
    // viewport: { width: 1280, height: 720 },
    // video: 'on-first-retry',
  },
    // timeout: 30000, //https://playwright.dev/docs/test-timeouts
    // expect: {
      /**
       * Maximum time expect() should wait for the condition to be met.
       * For example in `await expect(locator).toHaveText();`
       */
      // timeout: 10000,
    // },

  /* Folder for test artifacts such as screenshots, videos, traces, etc. */
  // outputDir: 'test-results/',

  /* Configure projects for major browsers */
  projects: [
    {
      name: 'chromium',
      use: { 
        ...devices['Desktop Chrome'],
        // viewport: { width: 1280, height: 720 },
      },
    },

    {
      name: 'firefox',
      use: { ...devices['Desktop Firefox'] },
    },

    {
      name: 'webkit',
      use: { ...devices['Desktop Safari'] },
    },

    {
      name: 'all-browsers-and-tests',
      use: { 
        baseURL: 'https://playwright.dev/',
         ...devices['Desktop Chrome']
      },
    },

    {
      name: 'all-browsers-and-tests',
      use: { 
        baseURL: 'https://playwright.dev/',
         ...devices['Desktop Safari']
      },
    },

    {
      name: 'all-browsers-and-tests',
      use: { 
        baseURL: 'https://playwright.dev/',
         ...devices['Desktop Firefox']
      },
    },

    // Example only
    {
      name: 'local',
      use: { 
        baseURL: baseEnvUrl.local.home,
      },
    },

    // Example only
    {
      name: 'ci',
      use: { 
         baseURL: process.env.CI
          ? baseEnvUrl.ci.prefix + process.env.GITHUB_REF_NAME + baseEnvUrl.ci.suffix //https://dev-myapp-chapter-2.mydomain.com
          : baseEnvUrl.staging.home,
      },
      /**
       * GitHub variables: https://docs.github.com/en/actions/learn-github-actions/variables
       * GitLab variables: https://docs.gitlab.com/ee/ci/variables/predefined_variables.html#predefined-variables-reference
       */
    },

    /* Test against mobile viewports. */
    // {
    //   name: 'Mobile Chrome',
    //   use: { ...devices['Pixel 5'] },
    // },
    // {
    //   name: 'Mobile Safari',
    //   use: { ...devices['iPhone 12'] },
    // },

    /* Test against branded browsers. */
    // {
    //   name: 'Microsoft Edge',
    //   use: { ...devices['Desktop Edge'], channel: 'msedge' },
    // },
    // {
    //   name: 'Google Chrome',
    //   use: { ..devices['Desktop Chrome'], channel: 'chrome' },
    // },
  ],

  /* Run your local dev server before starting the tests */
  // webServer: {
  //   command: 'npm run start',
  //   url: 'http://127.0.0.1:3000',
  //   reuseExistingServer: !process.env.CI,
  // },
});
```

### code snippets

```javascript
const { chromium } = require('playwright');
// https://playwright.dev/docs/api/class-elementhandle#element-handle-type

( async () => { // => function 
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

## Built in functions

### test func.

`test()`

takes two arguments: a string representing the title of the test, and an async function that defines the test itself. The async function receives an object with fixtures and optional TestInfo as its argument.

#### test() methods

`test.describe` is a method that declares a group of tests.\
It takes two arguments: a string that represents the title of the group, and the second argument is a callback function that contains all the tests belonging to this group. When `test.describe` is called, it immediately runs the callback function and any tests added in this callback will belong to this group.

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

### expect func.

`expect()`

To make an assertion, call `expect(value)` and choose a matcher that reflects the expectation. There are many generic matchers like `toEqual`, `toContain`, and `toBeTruthy` that can be used to assert any conditions.\
[https://playwright.dev/docs/test-assertions](https://playwright.dev/docs/test-assertions)
