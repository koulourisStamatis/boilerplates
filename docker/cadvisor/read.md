# cAdvisor Docker Compose Setup

This setup uses Docker Compose to run **cAdvisor** (Container Advisor), which is used to monitor and analyze resource usage and performance characteristics of running containers. For more information about cAdvisor, visit the official cAdvisor page: [https://github.com/google/cadvisor](https://github.com/google/cadvisor).

## Prerequisites

- Docker installed
- Docker Compose installed

## File Structure

The following structure is recommended for organizing your project:

```plaintext
/
└── docker-compose.yml       # Docker Compose file for cAdvisor
