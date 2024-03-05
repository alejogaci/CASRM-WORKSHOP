# CASRM-WORKSHOP

Welcome to the Cloud Asset Risk Management workshop

# Introduction

Empower yourself with the knowledge to manage cyber risks effectively through a cloud-centric approach. Join us for an insightful workshop focused on discovering, assessing, prioritizing, and remedying both internal and external attack surfaces.ASRM for Cloud provides tailored hybrid cloud telemetry correlation, facilitating quicker detection and response times while equipping cloud and security teams with the tools to consistently uncover, identify, and prioritize risks.

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/beff492f-874f-4a0f-ac82-db8c28c4113b)

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/fbe3ac57-84bc-47f3-bfdd-a7641b11009f)


Here you'll find a set of challenges you'll need to solve as quickly as possible. You'll be given access to an AWS account and a Vision One account, which are integrated and have a deployed infrastructure.

# Prerequisites

Just bring your laptop and the desire to learn new things

# Main Stage

As a cloud cybersecurity analyst, you have been informed of a possible company data breach. The AWS team indicates for sure that there is a public S3 bucket, but that there are most likely more AWS services involved since they have bad security practices. Your task as responsible for the incident is to replicate the attack starting from the public S3 bucket, verify which other AWs services are involved. Use CASRM to verify the visual that it can give  of the infrastructure and identify these failures from the tool, also generate some remediations to mitigate the attack.

# Task 1 - From the beginning  

## Task Description:

You have been informed of a security breach of your AWS infrastructure. An indication is that there is a public s3 bucket with sensitive information, the best way to start is to verify what type of information has been publicly exposed.

## Task details:

Enter to Vision One console

Under Attack Surface Risk Management click on Cloud Posture Overview

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/f3c0d07d-1b1a-4644-a2e4-3a503d2d545c)

Click on “View All Checks”

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/fd4e1fff-e9d0-4d12-8886-013f8e81f699)

Then, use filter checks to look for AWS S3 service configuration failures

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/06b2af9d-7447-4b03-ad35-0158f9ff722c)

Look for buckets that do not comply with the “S3 Bucket Public Access Via Policy” rule, look at the s3 IAM permissions shown in the rule to verify which bucket allows the files it has stored to be listed 

List the bucket via URL from a web browser (Not from the AWS console).

Note: Always use conformity to verify and identify bucket permissions, if you try to do it from the AWS gui it will not work

## Flag

What is the name of the file with sensitive information that was exposed to the Internet ?

## hints

Take a look to this

https://docs.aws.amazon.com/AmazonS3/latest/userguide/VirtualHosting.html#virtual-hosted-style-access

# Task 2 - Being the hacker  

## Task Description:

You found that file has been exposed to the internet, is it possible to download the information?

## Task details:

Try to download the file and check what kind of information is there

## Flag

The password for the user admin found in the file 

# Task 3 - Correlation 

## Task Description:

After having found the credentials of a database, it would be good to ask ourselves the question, do we have any other AWS service exposed to the internet?

## Task details:

Enter to Vision One console

Under Attack Surface Risk Management click on Cloud Posture Overview

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/f3c0d07d-1b1a-4644-a2e4-3a503d2d545c)

Click on “View All Checks”

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/fd4e1fff-e9d0-4d12-8886-013f8e81f699)

Then, use filter checks to look for AWS EC2 service configuration failures

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/06b2af9d-7447-4b03-ad35-0158f9ff722c)

Look for EC2 instances that do not comply with the “EC2 Instance Not In Public Subnet” rule

## Flag

 EC2 Instance ID  public to internet

# Task 4 - Get inside 

## Task Description:

Public EC2 instances are one of the most common breaches that exist and present a great risk to organizations as they are an easy entry point for attackers.After you have found a password in a file exposed to the internet and know that there is also a EC2 instance exposed, you should try to access the server.

## Task details

Enter the AWS console.

Can you see the EC2 isntance information?

Is there any public IP ?

Use AWS cloudshell to acces the EC2 instance via SSH.

## Flag

Kernel Version of the EC2 isntance

## Hints.

Try to acces to the instance with the usernames and passwords that you found in task 1

# Task 5 - The Bat signal

## Task Description:

One of the most common ways to expose websites to the internet on AWS is to use S3 to store static content (usually html files) and expose them through CloudFront. Unfortunately, many organizations accidentally leave unnecessary permissions on buckets so that hosted websites can be compromised.
One of your organization's internal websites has been compromised during the attack, the cybercriminals have changed the image of the site to one of Batman.

## Task details

Go to the web page url

The site needs a username and password to be accessed, you can try some of the ones you found in Task 1, once you access the site, can you determine what is the name of the file that contains the website image?

## Flag

Enter the file name

## Hint

From web browser, view source code

# Task 6 - Being the hacker

## Task Description:

Unfortunately, the s3 bucket that is hosting the website has been configured with permissions so that anyone can upload files. Can you identify which one it is?

## Task details

Enter to Vision One console

Under Attack Surface Risk Management click on Cloud Posture Overview

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/f3c0d07d-1b1a-4644-a2e4-3a503d2d545c)

Click on “View All Checks”

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/fd4e1fff-e9d0-4d12-8886-013f8e81f699)

Then, use filter checks to look for AWS EC2 service configuration failures

![image](https://github.com/alejogaci/CASRM-WORKSHOP/assets/37232597/06b2af9d-7447-4b03-ad35-0158f9ff722c)

Looks for buckets that do not comply with the “S3 Bucket Public Access Via Policy” rule.

Try to find if there is a bucket that lets you upload files.

## Flag

The name of the bucket


# Task 7 - Being the hacker

## Task Description:

Try to replace the image left by the cyber attackers with another in order to restore the site and replicate what they did

Go to cloudshell 

Download any image. 

User curl to make a PUT resquest to the bucket to upload the file. (Remember you need to replace the batman image)

Go to Web page url and check that the website is updated with the new image.

Click on “Click to reveal the flag”

## Flag

Message from “Click to reveal the flag” button

## Hint

need help ? you can ask for it




