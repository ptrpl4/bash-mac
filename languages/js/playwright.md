# Playwright

## Installation

#### Requirements&#x20;

node.js&#x20;

npm

```bash
# Run from your project's root directory
npm init playwright@latest
# Or create a new project
npm init playwright new-project
```

notes

```
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

run

```
npx playwright test
```
