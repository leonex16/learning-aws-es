# Elastic Container Service ( ECS )

## Introduction

Fully-managed **container** orchestration service.
Highly secure, reliable, and scalable way to
run containers

## Components of ECS

- **Cluster**
  - Multiple EC2 instances which will house the docker
container
- **Task Definition**
  - A JSON file that defines the configuration of ( upto 10 )
containers you want to run
- **Task**
  - Launches containers defined in Task Definition.
Tasks do not remaining running once workload is complete
- **Service**
  - Ensures tasks remaining running eg. web-apps servers
- **Container Agent**
  - Binary on each EC2 instance which monitors,
starts and stops tasks

## Creating an ECS Cluster

To create an ECS cluster in aws console, the following steps
must be taken:

1. Create Cluster
2. Choose between use spots or on demand
3. Choose EC2 instance type
4. Number of instances
5. EBS Storage Volume
6. EC2 can be **Amazon Linux 1** or **Amazon Linux 2**
7. Assign an IAM Role
8. Option to turn on CloudWatch Container Insights
9. *Choose a Key Pair

*\*You can SSH into on EC2 Container Instance and make
changes but its not generally recommended*

<div
style="
display: grid;
grid-template-columns: repeat(2, 1fr);
gap: 1rem">
<img
  src="https://i.postimg.cc/qMJs0Vnx/image.png"
  alt="Step 2" />
<img
  src="https://i.postimg.cc/8cP78G3F/image.png"
  alt="Steps 3, 4, 6" />
<img
  src="https://i.postimg.cc/4N0m0r1d/image.png"
  alt="Step 5" />
<img
  src="https://i.postimg.cc/rp1sKz20/image.png"
  alt="Step 7" />
<img
  src="https://i.postimg.cc/rsmwnJ0x/image.png"
  alt="Step 8" />
<img
  src="https://i.postimg.cc/0NPxXfhj/image.png"
  alt="Step 9" />
</div>

## Task Definition File

<div style="display: flex; gap: 1rem">
  <img
    src="https://i.postimg.cc/28RgHV8T/image.png"
    alt="Task Definition File"
    style="order: 2; width: 50%;" />
  <div style="order: 1;">
  You can define multiple containers within
  a task definition

  The ( docker ) <span class="text-red">**images**</span>
  can be provided either via **ECR** or an official
  docker repository, eg. Docker Hub

  You must have one <span class="text-red">**essential**</span>
  container. If this container fails or stops than all
  containers will be stopped

  AWS has a wizard to create Task Definitions instead
  having to create a file by hand
  </div>
</div>

## Elastic Container Registry ( ECR )

A fully-managed Docker container registry that makes
it easy for developers to **store**, **manage**,
and **deploy** Docker container images

<img
  src="https://i.postimg.cc/NMChdcjt/image.png"
  alt="Flow ECR" />

<style>
.text-red {
  color: red;
}
</style>
