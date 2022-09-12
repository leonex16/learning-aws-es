# CI/CD

Automated methodologies that **prepare**, **test**, **deliver**
or **deploy** code onto production server

## Introduction

### CI/CD Models

- **Production** - Is the live server where real paying users
are using the platform
- **Staging** - Is a private server do a final manual test
as a customer ( QA ) before deploying to production

### Steps on CI/CD

`Code > Build > Integrate > Test > Release > Deploy`

- **Code until Test**
  - Continuous integration ( CI )
  - Automatically reviews of developer's code
- **Code until Release**
  - Continuos Delivery ( CD )
  - Automatically prepare developer's code for release to production
- **Code until Deploy**
  - Continuos Deployment ( CD )
  - Automatically deploy code as soon as developer pushes
  code and if all test pass

## Continuous Integration

The practice of automating the **integration of code changes**
from multiple contributor into a single software project

This encourages small changes more frequently. Each commit
triggers a build during which tests are run that help to identify
if anything was broken by the changes

You can use the following AWS services:

- **CodeCommit** - Store to repository
- **Lambda** -  A webhook is trigger and tells lambda to run
- **CodeBuild** - Create a new build server
- **S3 Bucket** - Report back result ( report )

## Continuous Delivery

The practice of automating the preparation of code to be released
to production or staging branches. You are preparing the codebase
for deployment. **Deployment is still a manual process**

You can use the following AWS services:

- **CodeCommit** - Store to repository
- **Lambda** -  A webhook is trigger and tells lambda to run
- **CodeBuild** - Create a new build server
- **S3 Bucket** - Report back result ( report )

## Continuous Deployment

The same as Continuous Delivery but **automatically deploys**
changes to production

- **CodeCommit** - Store to repository
- **Lambda** -  A webhook is trigger and tells lambda to run
- **CodeBuild** - Create a new build server
- **S3 Bucket** - Report back result ( report )
- **CodeDeploy** - See changes to master branch and automatically
deploys to production servers

## Cheat Sheet

- CI/CD is automated methodologies that **prepare**, **test**,
**deliver** or **deploy** code onto a servers
- **Production** an environment which is entended to be used
by paying users
- **Staging** An environment which is intended to simulate a
production environment for last stage debugging
- **Continuous Integration ( CI )**
  - Automating the review of developer's code
  - Eg. Run test suites with a build server like CodeBuild
- **Continuous Delivery ( CD )**
  - Automating the preparation of the developer's code for release
  - Eg. Run test suites with a build server ( CodeBuild ) and
  if test pass create pull request or merge branch into staging
- **Continuous Deployment ( CD )**
  - Automatically deploying developer's code which ready
  for release
  - Eg. Automatically merge pull requests will all tests passing
  and deploying into production
  - Continuous deployment can refer to the entire pipeline
  Eg. CodePipeline using CodeCommit + CodeBuild + CodeDeploy

<style>
.text-red {
  color: red;
}
</style>
