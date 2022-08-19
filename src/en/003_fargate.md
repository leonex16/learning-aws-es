# Fargate

## Introduction

**Serverless Containers**. Do not worry about servers.
Run containers, and pay based on duration and consumption

- You can an **empty** ECS cluster ( no EC2's provisioned )
and then launch Tasks as Fargate
- You **no longer have to**
<span class="text-red">**provision**</span>,
<span class="text-red">**configure**</span>, and
<span class="text-red">**scale**</span> clusters
of EC2 instances to run containers
- You are charged for at least one minute and after its by
the second
- You pay based on duration and consumption

<img
  src="../../public/images/fargate/ecs_vs_fargate.png"
  alt="ECS vs Fargate" />

## Configuring Fargate Tasks

<img
  src="../../public/images/fargate/configuring_fargate_tasks.png"
  alt="Configuring Fargate Tasks" />

## Fargate vs Lambda

Lambda and Fargate appear very similar, but there are
few key differences

|                 | **Fargate**                                    | **Lambda**                                           |
|-----------------|------------------------------------------------|------------------------------------------------------|
| **Cold Starts** | Yes ( shorter )                                | Yes                                                  |
| **Duration**    | As long as you want                            | 15 min                                               |
| **Memory**      | Up to 30Gb                                     | Up to 3Gb                                            |
| **Containers**  | You provide your own containers                | Limited to standardize containers                    |
| **Integration** | More Manual                                    | Seamlessly integrates with other serverless services |
| **Pricing**     | Pay at least 1 min and every additional second | Pay pe 100ms                                         |

<style>
.text-red {
  color: red;
}
</style>
