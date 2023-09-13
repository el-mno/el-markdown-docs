---
title: AWS Fargate and Lambda Comparison
---

# AWS Lambda and AWS Fargate: Which one is right for you?
_Last Modified: 2023-09-13_

### Overview
**AWS Lambda** and **AWS Fargate** are both serverless computing solutions offered by Amazon Web Services (AWS) that serve distinct advantages depending on your use case. Let's take a closer look as to where and when each of the services shine.

## Key Attributes
### AWS Lambda
* 15 minute limitation for processes (cannot be altered within AWS)
* Concurrency limit for all functions in a region: 1000 (can be changed by AWS)

### AWS Fargate
* Containerized jobs: Docker Containers + Elastic Container Service