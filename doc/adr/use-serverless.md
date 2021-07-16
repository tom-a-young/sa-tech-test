# Use Serverless to Handle Lambda Deployment

* Date: 2021-07-16 

## Context and Problem Statement

We want to deploy and manage lambdas to facilitate our App. We ideally want to do this in a quick and efficient manner which is easy to work with.

## Decision Drivers 

* Ease of use
* Separation of concerns

## Considered Options

* Serverless
* Terraform

## Decision Outcome

We have chosen to use serverless for lambda deploys as it allows us to deploy them separately to our terraform stacks and tweak configuration pertaining only to that lambda without affecting a whole terraform stack.

