# Use Terraform for AWS Services

* Date: 2021-07-16

## Context and Problem Statement

We want to be able to deploy our stacks with an IaC pattern to ensure resilience and easy customisability.

## Decision Drivers 

* Cost
* Maintainability
* Ease of Use

## Considered Options

* CloudFormation
* Terraform

## Decision Outcome

We have chosen to use Terraform for managing AWS services as it is a mature platform that can be easily customised to fit our stacks. It is well integrated with AWS, but could be used as a basis for switching to another service provider, should that become necessary. 

