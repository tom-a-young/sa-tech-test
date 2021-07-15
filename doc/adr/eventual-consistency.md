# Use Eventually Consistend Reads on Video Metadata Table

* Date: 2021-07-15 

## Context and Problem Statement

We want to save money on our DynamoDB implementation and thus we want to limit the amount of Read and Write capacity units used.

## Decision Drivers 

* Costs of DB

## Decision Outcome

We have chosen to use eventually consistent reads, as these consume only half an RCU per read, and it is not essential that reads from the Video Metadata table are immediately consistent.

