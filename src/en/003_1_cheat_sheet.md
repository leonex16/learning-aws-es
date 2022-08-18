# ECS and Fargate Cheat Sheet

- Fully-managed **container** orchestration service.
Highly secure, reliable, and scalable way to
run containers
- **Components of ECS**
  - **Cluster:** Multiple EC2 instances which will house
  the docker container
  - **Task Definition:** A JSON file that defines
  the configuration of ( upto 10 ) containers you want to run
  - **Task:** Launches containers defined in Task Definition.
  Tasks do not remaining running once workload is complete
  - **Service:** Ensures tasks remaining running
  eg. web-apps servers
  - **Container Agent:** Binary on each EC2 instance which monitors,
  starts and stops tasks
- **Elastic Container Registry ( ECR )** A fully-managed Docker
container registry that makes it easy for developers
to **store**, **manage**, and **deploy** Docker container images
- **Fargate** is **Serverless Containers**. Do not worry
about servers. Run containers, and pay based on duration
and consumption
  - Fargate has **Cold Starts** so if this an issue for
  you then use ECS
  - **Duration** As long as you want
  - **Memory** Up to 30Gb
  - **Containers** You provide your own containers
  - **Integration**More Manual
  - **Pricing** Pay at least 1 min and every additional second
