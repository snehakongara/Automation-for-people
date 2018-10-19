# Automation-for-people
This repo contains code for deploying web service TO AWS using jenkins.

Below are the steps for building pipeline.

1.	Login to AWS console.
2.	You need to have CloudFormation ARN to create stack using repo from git.
3.	Using the microservice template we create roles and lambda functions to pre-create tests.
4.	Upload the main pipeline for the stack to be created with required SNS topics, s3, lambda functions for pre-create tests on the template code.
5.	Main pipeline fetches the code from CodeCommit and starts the pipeline. CodeCommit monitors repository for new or modified AWS CloudFormation template.
6.	An AWS lambda function launches the test stacks such as default test on template syntax.
7.	Once all the tests are successful it sends notification to the email provided to let you know the template is ready for manual approval in AWS CodePipeline.
8.	Once we approve it, the pipeline will invoke a lambda function that will deploy the template and store the data in S3(such as CloudWatch data).
9.	Taking the template S3 URL we create a stack, we will be able to view the page displaying “Automation for people”.
10.	For cleaning the pipeline, we have to delete the stacks created.

AWS console:
Public DNS: ec2-18-212-92-205.compute-1.amazonaws.com 
IPV4 public IP : 18.212.92.205
