---
title: Software Testing Lifecycle
publishedOn: 2021-12-22T00:00:00
updatedOn: 2021-12-22T00:00:00
tags: ['testing', 'qa', 'agile', 'develoment', 'topic' ]
description: Outline to lead a guided group learning session on the software testing lifecycle.
---

## Topics for Discussion

* What are the steps in the Software Testing Life Cycle?
* How does it fit into the Software Development Life Cycle?
* How does the “shift left” concept and Agile Testing affect the Software Development and Software Testing Life Cycles?

### What are the steps in the Software Testing Life Cycle?

**_Prompt: What stages of the life cycle shown above do you think overlap with Cypress?_**

1. **Requirement Analysis:** Define the testable requirements of the application. 
    1. Detailed requirements report - what do we need to test? What are the priorities?
    2. Test automation feasibility report - how feasible is it to automate the testing of the requirements? What will need manual testing?
    3. Requirements Traceability Matrix - How do we trace testing activities back to the requirements?
        1. “Traceability” here means the ability to trace back artifacts from their requirements. **For instance, having traceability in the software development process means that the organization should be able to trace each commit in its codebase back to its original requirements.**
2. **Test Planning:** Prepare test plan documentation that outlines the expected resources, tools, environments, tasks, and teams to complete the testing, as well as any training requirements.
3. **Test Case Design and Development:** The definition, organization, and writing/coding of the test cases.
4. **Test Environment Setup:** Software and hardware configuration, along with test data setup, are the main components of this phase. Environments should be prioritized based on those used by the end-user. The main deliverable in this stage is a complete strategy for test environment management.
5. **Test Execution:** Tests are executed based on test plan. Any deviations from expected behavior (defects, bugs) are identified, logged, and reported to the development team for resolution.
6. **Test Closure:** Review test results to assess overall quality and test strategy and document lessons learned.


### How does the STLC fit into the Software Development Life Cycle?

The software testing life cycle (STLC) is a child process of the software development life cycle (SDLC) that is focused on finding defects and reporting them to the development team to resolve.

The steps of the Software Testing Life Cycle typically take place WITHIN the “Test” step of the Software Development Life Cycle. The STLC represents a more detailed breakdown of the Test phase.

It’s goals are different in that it is focused on finding defects, as opposed to building a product. In traditional organizations, the STLC is completed by a testing team, whereas the overall SDLC is managed and completed by a development team.

### Testing in Development

**Shift-left testing: Testing during the development process to find bugs earlier and reduce bugs in production**

Under this concept, we are literally shifting testing “left” up the SDLC so it happens during the development phase. This means testing can be done by test engineers working closely with developers, or by developers themselves.

**By testing early and often, a project can reduce the number of bugs and increase the quality of the code. The goal is to not find any critical bugs during the deployment phase that require code patching.**

Most of the time, it means developing and executing more automated testing of the UI and APIs.

Types of Testing at the Development Level:

* Static Testing (Typescript, linting, etc. Done in IDE)
* Code Review
* Unit Testing
* Basic Functionality Testing
* Test Driven Development

**_Prompt: What impacts have you seen to the testing lifecycle when there is no dedicated testing team? Do you think developers test differently than QA/Test Engineers?_**

### Agile Testing

The agile testing process is a continuous process rather than being sequential. The testing begins at the start of the project and there is ongoing integration between testing and development.  The common objective of agile development and testing is to achieve a high product quality.


* Testing is continuous
* Continuous feedback
* Tests performed by the whole team
* Decrease time of feedback response
* Simplified & clean code
* Less documentation
* Test Driven

**_Prompt: What do you think are some of the benefits of Agile Testing?_**

### Resources

* [What Is the Software Testing Life Cycle? A Complete Guide](https://www.testim.io/blog/software-testing-life-cycle/)
* [Software Testing Life Cycle (STLC)](https://www.geeksforgeeks.org/software-testing-life-cycle-stlc/)
* [What does Software Development Life Cycle (SDLC) mean?](https://www.techopedia.com/definition/22193/software-development-life-cycle-sdlc)
* [Difference between SDLC and STLC](https://www.geeksforgeeks.org/difference-between-sdlc-and-stlc/)
* [Agile Testing Methodology - Methods, Principles & Advantages](https://reqtest.com/testing-blog/agile-testing-principles-methods-advantages/)
* [What Is Shift Left Testing? A Guide to Improving Your QA](https://www.testim.io/blog/shift-left-testing-guide/)
* [5 key software testing steps every engineer should perform](https://techbeacon.com/app-dev-testing/5-key-software-testing-steps-every-engineer-should-perform)