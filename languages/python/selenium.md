# Selenium

## Preparing

requirements:

* git
* python3
* pipenv

File structure

* Project\_name
  * tests
    * conftest.py - config file
    * test\_name.py - test file
    *

WebDrivers

Chrome - [https://chromedriver.chromium.org/home](https://chromedriver.chromium.org/home)

Gecko - [https://github.com/mozilla/geckodriver/releases](https://github.com/mozilla/geckodriver/releases)

## Test Fixtures

based on pytest

```python
tests/conftest.py

import pytest
from selenium import webdriver
from selenium.webdriver.chrome.service import Service

@pytest.fixture
def browser():

    # Initialize the test driver instance
    s = Service('./chromedriver')
    browser = webdriver.Chrome(service = s)

    # Add 10 sec wait
    browser.implicitly_wait(10)

    # Return the test driver instance
    yield browser

    # Quit the test driver instance
    browser.quit()

@pytest.fixture
def gecko():

    # Initialize the test driver instance
    s = Service('./geckodriver')
    browser = webdriver.Firefox(service = s)

    # Add 10 sec wait
    browser.implicitly_wait(10)

    # Return the test driver instance
    yield browser

    # Quit the test driver instance
    browser.quit()
```
