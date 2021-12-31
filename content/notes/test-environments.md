---
title: "Test Environments"
publishedOn: 2021-12-23T00:00:00
tags: ["testing", "qa", "CI", "Docker", "test automation", "environments", "topic"]
description: "Outline to lead a guided group learning session on software test environments."
---

## Topics for Discussion

* What is a test environment?
* How are test environments created?
* What must be considered when designing, creating, and managing environments?

### What is a test environment?

**_Prompt: How do you define an environment? What are some types of environments you’ve worked with?_**

**In software deployment, an environment, or tier is a computer system or set of systems in which a computer program or software component is deployed and executed.**

Examples:
* development
* test/QA
* staging
* production

A **development environment** is used during the process of writing software and is typically a local environment on the software developer’s machine.

A testing engineer uses **test environments** to test a very specific part of an application. It often involves a different configuration and data setup. It could include the entire deployed application or only a subset required for testing (i.e. API server with no front end used for API testing).

A **staging environment** replicates the production environment that will host the live version of your application. It’s crucial that your staging environment is an exact replica of your production environment.

**While a test environment is focused on testing individual components, the staging environment is focused on testing the whole application.**

### How are test environments created?

Things required to create an environment:

* A machine (physical or cloud) to host the deployed application
* Configuration requirements for the environment
    * Machine type
    * Operating system
    * Dependencies, including browsers
* Source code to deploy to the environment
* Ports defined for the required parts of the application
    * Front end application
    * API server
    * Database (if needed)
* Data for the environment
* A set of instructions to configure the environment and deploy the application
    * YAML 
    * CI configuration
    * Manual deployment

There may be specific configuration, security requirements, deployment steps, data requirements, or even differences to source code that may differ between test and production or staging environments. 

**_Prompt: What methods have you seen for managing the creation of environments?_**

The best way to simplify the process of creating identical environments is by using **Docker**.

From [Using Docker to manage and replicate test environments](https://testcollab.com/blog/using-docker-to-manage-and-replicate-test-environments/):

“Docker lets you build containers. Think of a container as your pre-configured, ready to use, super-fast, clone-able application runtime environment. So I’ll just have to configure my container once and I can use it to launch tens or hundreds of my application copies. And they’ll live separately.”

**_Example: Cypress Real World App_**

[https://github.com/cypress-io/cypress-realworld-app/blob/develop/.github/workflows/main.yml](https://github.com/cypress-io/cypress-realworld-app/blob/develop/.github/workflows/main.yml)

[https://github.com/cypress-io/cypress-realworld-app/blob/develop/.circleci/config.yml](https://github.com/cypress-io/cypress-realworld-app/blob/develop/.circleci/config.yml)

[https://github.com/cypress-io/cypress-realworld-app/blob/develop/package.json#L172](https://github.com/cypress-io/cypress-realworld-app/blob/develop/package.json#L172)

### What must be considered when designing, creating, and managing environments?

##### Designing

* What type(s) of testing will be performed against the environment?
* What part(s) of the application are required to perform the planned testing?
* Will we have a single environment for multiple types of testing or multiple environments?
* How many tests will be performed against the environment?
* What are the performance requirements of the environment to support the planned testing?
* What physical machine resources are required to support the testing and application?
* What hardware, operating system, and browser requirements must be covered by the test environment(s)?
* What security protocols will be used to ensure proper access and usage of environment(s)?
* What data is required to seed the environment?

##### Creating

* How long does it take to build/deploy a test environment?
* How frequently will the environment(s) be created or updated?
* How long will the environment be online or will it be continuously deployed?
* How will we seed the environment for each deployment?
* What environment variables will be needed or changed at run time? (Cypress, OS, CI)

##### Managing

* How do we sanitize or reseed data in the environment?
* Who is responsible for monitoring the environment stability, performance, and resource usage?
* What is the strategy for removing environments that are no longer needed?
* How do we audit existing machine/OS/browser requirements and ensure environments are consistent with requirements?

**_Prompt: What else would you add as considerations for environments? What have customers encountered that have caused issues?_**

### Resources

* [Test Environments 101: Definition, Types, and Best Practices - LaunchDarkly](https://launchdarkly.com/blog/test-environments-101-definition-types-and-best/)
* [Why Teams Should Consider Parallel Automated Functional Testing](https://saucelabs.com/resources/articles/why-teams-should-consider-parallel-automated-functional-testing)
* [What Is a Test Environment? A Guide to Managing Your Testing](https://www.testim.io/blog/test-environment-guide/)
* [2019 DZONE Research Guide to Automated Testing](https://drive.google.com/file/d/1w3TVDFTVwDsZ3ITuF5XlH-Yclcix71TH/view?usp=sharing)
* [You Can Have It All: How to Maximize Your Software Testing Coverage](https://saucelabs.com/resources/articles/you-can-have-it-all-how-to-maximize-your-software-testing-coverage)
* [Using Docker to manage and replicate test environments](https://testcollab.com/blog/using-docker-to-manage-and-replicate-test-environments/)