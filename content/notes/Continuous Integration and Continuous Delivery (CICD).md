---
title: "Continuous Integration and Continuous Deployment"
enableToc: true
tags:
- CICD
- DevOps
---
## CI/CD
CI/CD automates much or all of the manual human intervention traditionally needed to get code from a commit into production. With a CI/CD pipeline development teams can make changes to code that are then automatically tested and pushed out for delivery and deployment. 

The aim is that progress should move forward and, if possible, never to go back to fix problems again. Problems should be identified and fixed when and where they were introduced. For this to occur, developers need fast feedback loops which is achieved through automated tests that will validate if the code works as intended before moving onto the next stage.

As applications grow larger, CI/CD can decrease development complexity and help scale applications safely. 

## Continuous Integration (CI)
Continuous Integration is the practice of integrating all code changes into the main branch early and often, automatically testing and building each change when you commit. By merging changes frequently, the risk of the possibility of code conflicts, bugs and security issues can be identified much earlier making it easier to diagnose.    

## Continuous Delivery (CD)
Continuous delivery is the practice that automates the infrastructure provisioning and application release process. Once code has been tested and built in CI, CD ensures its releasable and able to deploy to any environment at any time. This can include provisioning infrastructure to deploying the application to the testing or production environment automatically. The purpose is to ensure that minimal effort is required to deploy new code. 

## Continuous Deployment
Continuous Deployment is the practice that every change that passes all production pipeline criteria is released to the customers. This is done automatically without human intervention. This allows code to be delivered frequently to get feedback from business teams or customers. 

Common deployment approaches are:
- Blue-Green deployment
- Canary deployment

![[files/cicd.png]]
## Continuous Testing
Continuous testing is a practice where tests are automatically run during the CI/CD process in order to ensure that the application is still working as expected. 
- [[notes/Unit Testing|Unit Testing]], which checks that individual units of code work as expexted.
- [[notes/Integration Testing|Integration Testing]], which verifies how different modules or services within an application work together
- [[notes/Regression Testing|Regression Testing]], which is performed after a bug is fixed to ensure that specific bug wont occur again

## References
- https://about.gitlab.com/topics/ci-cd/
- https://thenewstack.io/a-primer-continuous-integration-and-continuous-delivery-ci-cd/
- https://www.redhat.com/en/topics/devops/what-is-ci-cd
- https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment