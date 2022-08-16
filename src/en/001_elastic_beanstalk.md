# Elastic Beanstalk ( EBS or EB )

## Introduction

Quickly deploy and manage web-apps on AWS without worrying
about the underlying infrastructure. It is a Platform as a
Service ( PAAS )

### What is Platform as a Service?

A platform allowing customers to develop, run, and manage
applications without the complexity of building and maintaining
the infrastructure typically associated with developing and
launching an applications

It is so easy that choose a platform, upload your code and
it runs with little knowledge of the infrastructure.

**Not Recommended for
<span class="text-red">Production</span>
Applications** ( only applies to big companies)

EBS is powered by a CloudFormation template setups for you:

- Elastic Load Balancer
- Autoscaling Groups
- RDS Database
- EC2 Instance pre-configured ( or custom ) platforms
- Monitoring ( CloudWatch, SNS )
- In-Place and Blue/Green deployment methodologies
- Security ( rotates passwords )
- Can run **Dockerized** environments

## Supported Languages

- Ruby ➡️ Rails
- Python ➡️ Django
- PHP ➡️ Laravel
- Java ➡️ Spring
- NodeJs ➡️ Express

## Web vs Worker Environment

When you first create a Elastic Beanstalk applications,
you have to choose an environment and you are choosing
between web versus worker. So if you are need to build
a web application, it can choosing a web environment,
but if you need to run background jobs, you can choose
a work environment.

A lot of the cases when you are building web apps,
you are going to make to environments, you can actually
make both of these one web and one worker, and they are
going to be interconnected together.

## Web Environment Types

- Single Instance Env
  - Still uses an ASG but desired capacity set to 1 to ensure
  server is always running
  - No ELB to save on cost
  - Public IP address has to be used to route traffic to server
- Load Balanced Env
  - Uses ASG and set to scale
  - Uses an ELB
  - Designed to scale

## Deployment Policies

There are the deployment policies available with Elastic Beanstalk

| **Deployment Policies**           | **Load Balanced Env** | **Single Instance Env** |
|-----------------------------------|:---------------------:|:-----------------------:|
| **All at once**                   | 🟢                    | 🟢                      |
| **Rolling**                       | 🟢                    | 🔴                      |
| **Rolling with additional batch** | 🟢                    | 🔴                      |
| **Immutable**                     | 🟢                    | 🟢                      |

### All At One

1. Deploys the new app version to all instances at the same time
2. Takes all instances **out of service**
while the deployment processes
3. Servers become available again

The <span class="text-green">**fastest**</span> method but
also the most <span class="text-red">**dangerous**</span>
deployment method

#### In Case of Failure

You need to roll back the changes by re-deploying
the original version again to all instances

### Rolling

1. Deploys the new app version to a batch of instances at a time
2. Takes batch's instances out of service while
the deployment processes
3. Reattaches updated instances
4. Goes onto next batch, taking them out of service
5. Reattaches those instances ( rise and repeat )

#### In Case of Failure

You need to perform an additional rolling update in order
to roll back the changes

### Rolling with Additional batch

1. Launch ne instance that will be used to replace a batch
2. Deploy update app version to new batch
3. Attach the new batch and terminate the existing batch

Rolling with additional batch's ensure our capacity
is never reduced. <span class="text-red">This is important
for applications were a reduction in capacity could cause
availability issues for users</span>

#### In Case of Failure

You need to perform an additional rolling update in order
to roll back the changes

### Immutable

1. Create a new ASG group awith EC2 instances
2. Deploy the updated version of the app on the new EC2 instances
3. Point the ELB to the new ASG and delete the old ASG which
will terminate the old EC2 instance

The <span class="text-blue">**safest way**</span>
to deploy for critical applications

#### In Case of failure

You just terminate the new instances since the existing
instances still remain

## Deploy Methods

| **Method**                        | **Impact of failed deployment**                                                                    | **Deploy time** | **Has Downtime?** | **DNS Change?** | **Roll back process** | **Code deployed to instances** |
|-----------------------------------|----------------------------------------------------------------------------------------------------|-----------------|:-----------------:|:---------------:|:---------------------:|:------------------------------:|
| **All at once**                   | Downtime                                                                                           | 🕛              | Yes               | No              | Manual                | Existing                       |
| **Rolling**                       | Single batch out of service; any successful batches before failure running new application version | 🕛🕛            | No                | No              | Manual                | Existing                       |
| **Rolling with additional batch** | Minimal if first batch fails; otherwise, similar to Rolling                                        | 🕛🕛🕛          | No                | No              | Manual                | New and Existing               |
| **Immutable**                     | Minimal                                                                                            | 🕛🕛🕛🕛        | No                | No              | Terminate New         | New                            |
| **Blue/Green**                    | Minimal                                                                                            | 🕛🕛🕛🕛        | No                | Yes             | Swap URL              | New                            |

## In-Place vs Blue/Green Deployment

In-Place and Blue/Green Deployment
<span class="text-red">are not definitive in definition</span>
and the context can change the scope of what they mean

### Possible Definitions of In-Place

- **Scope of Elastic Beanstalk Env**
  - All the deployment policies provided by EB could be
  considered In-Place since they are within the scope of a
  single EB environment
  - All at once, Rolling, Rolling and additional batch, and Immutable
- **Scope of the same server ( not replacing the server )**
  - Deployment policies which do not involve the server
  being replaced
  - All at once, Rolling, and Rolling and additional batch
- **Scope of an uninterrupted server**
  - Traffic is never routed away from
  the server ( taken-of-service ). Implements Zero-downtime
  deploys where Blue/Green occurs on the server
  - EB can not do this. Capistrano + Ruby on Rails + Unicorn
  is famous case of thi method of deployment

### Blue/Green Deployment in EB

<div style="display: flex; gap: 16px;">
  <img
    src="https://i.postimg.cc/jSw-qynQg/image.png"
    alt="Immutable ( In-Place )" />
  <img
    src="https://i.postimg.cc/HWhfXZZm/image.png"
    alt="Immutable ( In-Place )" />
</div>

*\*Blue/Green with EB requires that your database
are **outside** of EB envs because envs are terminated
with loss of all their resources*

## Configuration Files

EB environments can be customized using configuration files

- **.ebextensions** is a hidden folder called at the root
of your project which contains the config files
- **.config** is the extension for the config files which need
to be store in .ebextensions

## Env Manifest

File called **env.yml** which is stored at the root of your project

When creating new EB env, this file allows you to configure
the defaults such as:

- The name of the env ( EnvironmentName )
- Choosing the stack solution ( SolutionStack )
- Etc

*\*This file format includes support for environment groups.
To use groups, specify the environment name in the manifest
with a "+" symbol at the end. E.g. exapro-prod+*

## Linux Server Configuration

<img
src="https://i.postimg.cc/vTSNGBKk/image.png"
alt="Linux Server Configuration" style="width: 100%;" />

## EB CLI

```bash
aws elasticbeanstalk help
```

## EB Custom Image

When you create an EB environment, you can specify an AMI
to use instead of the standard EB AMI

A custom AMI can
<span class="text-red">**improve provisioning times**</span>
when instances are launched in your environment

If **you need to install a lot of software** that
is not included in the standard AMIs.

### Steps to Use a Custom Image

<img
  src="https://i.postimg.cc/7Lw154SL/image.png"
  alt="Steps to Use a Custom Image" style="width: 100%;" />

## Configuration RDS

A database can added **inside** or **outside** your EB Env

### Inside EB Env

- Intended for generally
<span class="text-red">**development**</span> envs
- You crate the database within B
- When the EB env is terminated the database will also be terminated

### Outside EB Env

- Intended for <span class="text-red">**production**</span> envs
- You create the database from RDS separate for EB
- When the EB env is terminated the database will remain

## Cheat Sheet

- Elastic Beanstalk handles the deployment,
from capacity provisioning, load balancing, auto-scaling
to application health monitoring
- When you want to run a web-application but you do not want
to have think about the underlying infrastructure
- It cost nothing to use EB ( only the resources it
provisions e.g. RDS, ELB, EC2 )
- Recommended for test or development apps.
Not recommended for production use ( big companies )
- You can choose from the following pre-configured
platforms: Java, .Net, PHP, Node Js, Python, Ruby, Go, and Docker
- You can run containers on EB either in Single-container
or Multi-container, these containers are running on ECS
instead of EC2
- You can launch either a **Web Environment** or a **Worker Environment**
  - **Web Environment**
    - **Single-Instance Env** launches a single EC2 instance,
    an EIP ( Elastic IP addresses ) is assigned to the EC2 instance
    - **Load Balanced Env** launch EC2s behind an ELB managed
  - by an ASG
  - **Worker Environment** creates an SQS queue,
  install the SQS daemon on the EC2 instances, and
  has ASG scaling policy which will add or remove instances
  based on queue size
- Eb has the following **Deployment Policies**:
  - **All at once** takes all servers out-of-service,
  applies changes, puts servers back-in-service, Fast, has downtime
  - **Rolling** updates servers in batches, reduced capacity
  based on batch size
  - **Rolling with additional batch** adds new servers in
  batches to replace old, never reduces capacity
  - **Immutable** creates the same amount of servers,
  and switches all at once to new servers, removing old servers
- **Rolling deployment polices require an ELB** so cannot be
used with Single-Instance Web Environments
- In-Place deployment is when deployment occurs within
the environment, all deployment policies are In-Place
- Blue/Green is when deployment swaps environments ( outside
an environments ). When you have external resources such as
RDS which cannot be destroyed its suited for Blue/Green
- **.ebextensions** is a folder which contains all
configuration files
- With EB you can provide a **Custom Image** which can improve
provisioning times
- If you let EB create the RDS instance, that means when
you delete your env, it will delete the database, This setup
is intended for development and test environments
- **Dockerrun.aws.json** is similar to ECS Task Definition files
an defines Multi-container configuration

<style>
.text-green {
  color: green;
}
.text-blue {
  color: blue;
}
.text-red {
  color: red;
}
</style>
