# CloudTrail

Logs API calls between AWS services.
When you need to know **who to blame**

## Introduction

AWS CloudTrail is a service that enables **governance**,
**compliance**, **operational auditing**,
and **risk auditing** of your AWS account

AWS CloudTrail is used to **monitor API calls** and
**Actions** made on an AWS account

Easily identify which users and accounts made the
call to AWS eg.

- **Where** Source IP Address
- **When** EventTime
- **Who** User, UserAgent
- **What** Region, Resource, Action

<img
  src="../../public/images/cloudtrail/introduction.png"
  alt="Example" />

## Event History

CloudTrail is already logging by default and will collect logs
for **last 90 days** via **Event History**

if you need more that 90 days you need to create a **Trail**

Trails are output to S3 and do not have GUI like Event History.
To analyze a TRail you'd have to use **Amazon Athena**

## Trail Options

- A Trail can be set to **log to all regions**
- A Trail can be set to **across all accounts in an organization**
- You can **Encrypt your Logs** using Server Side Encryption
via Key Management Service ( SSE- KMS )
- We can ensure the Integrity of our logs to see if they
have been tampered we need to turn on
**Log File Validation**

## CloudTrail to CloudWatch

CloudTrail can be set to deliver events to CloudWatch log

## Management vs Data Events

### Management Events

Track management operations. Turned on by default.
Can't be turned off

- **Configuring security**
  - eg. IAM AttachRolePolicy API operations
- **Registering device**
  - eg. AWS EC2 CreateDefaultVpc API operations
- **Configuring rules for routing data**
  - eg. Amazon EC2 CreateSubnet API operations
- **Setting up logging**
  - eg. AWS CloudTrail API operations

### Data Events

Tracks specific operations for specific AWS services.
Data events are high volume logging and will result
in additional charges. **Turned off by default**

The two services that can be tracked is S3 and
Lambda. So it would track action such as:
GetObject, DeleteObject, PutObject

## Cheat Sheet

- CloudTail logs calls between AWS services
- **governance**, **compliance**, **operational auditing**,
and **risk auditing** are keywords relating to CloudTail
- When you need to know **who to blame** think CloudTail
- CloudTail by default logs event data for the past 90s days
via **Event History**
- To track beyond 90 days you need create **Trail**
- To ensure logs have not been tampered with you need to
turn on **Log File Verification** option
- CloudTail logs can be encrypted using **KMS**
- CloudTail can be set to log across all AWS accounts in
an Organization and all regions in an account
- CloudTail logs can be streamed to CloudWatch logs
- Trails are outputted to an S3 bucket that you specify
- CloudTrail logs two kinds of events: **Management Events**
and **Data Events**
- **Data Events** log data operations for resources
( S3, Lambda ) eg, GetObject, DeleteObject, PutObject
- Data Events are **disabled** by default when creating a Trail
- Trail logs in S3 can be analyzed using Amazon Athena

<style>
.text-red {
  color: red;
}
</style>
