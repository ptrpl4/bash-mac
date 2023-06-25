---
description: test/behavior-driven development
---

# 😎 TDD, BDD etc

## TDD

test-driven development

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

#### process

create unit test => run test (failed) => create feature code =>  run test (succeed) => refactor test/code => rerun test (succeed)

## BDD

behavior-driven development

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

* BDD encourages creating a ubiquitous language in the software development process, facilitating communication inside the team and organization.
* BDD is a user-centric approach. The process starts by thinking of scenarios from the user's perspective. This helps to ensure that the team delivers what brings the most value for the end user.
* Scenarios in BDD are written in plain English, using the Given-When-Then syntax.

```
Scenario: User wants to add an item to the TO-DO system with a past due date 
Given user is logged in 
And today is April 10th 2021 
When the user tries to add an item with a due date of April 5th 
The addition of the new item should fail
```

## **Acceptance TDD**&#x20;

ATDD is very similar to BDD. The difference between ATDD and BDD is that ATDD mainly focuses on accuracy of requirements, vs. BDD primarily focuses on user behavior.

## **Developer TDD**&#x20;

DTDD is simply the basic TDD approach where the developer writes the unit test before writing enough production code to fulfill those tests.
