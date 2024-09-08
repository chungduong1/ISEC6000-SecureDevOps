# ISEC6000-SecureDevOps
Secure DevOps
Nowady, e-commerce platforms are central to the growth of online retail, necessitating continuous innovation and agility. The ability to quickly build, deploy, and scale e-commerce solutions like websites, platforms, payment gateways, and applications has become crucial for businesses. However, this rapid development also introduces significant security challenges, with cyber threats becoming more sophisticated and prevalent.

This project focuses on equipping me with the necessary skills to design, deploy, and secure a modern e-commerce application using cutting-edge DevOps security practices. My goal is to build a scalable microservices architecture for the Saleor platform, an open-source, Python-based e-commerce solution. By leveraging tools such as Docker, Kubernetes, and Google Kubernetes Engine (GKE), I will ensure that each component of the application is isolated, manageable, and secure.

The project will involve setting up the foundational infrastructure, deploying the Saleor platform using Docker Compose within a Kubernetes environment, and implementing robust security measures. This includes securing Docker containers, scanning for vulnerabilities, and implementing runtime security controls. Continuous monitoring and logging will be integrated to provide real-time insights into the application's performance and security, ensuring proactive issue detection and resolution.

Additionally, I will document every aspect of the process, from setup and configuration to the implementation of security measures and monitoring solutions. This documentation will serve as a comprehensive guide, allowing others to replicate or build upon the work completed in this project.

The completion of this project will not only enhance my technical skills but also contribute to the broader field of secure e-commerce development by providing a detailed case study on the deployment and protection of a microservices-based e-commerce application.
## About

### What is Saleor Platform?

Saleor Platform is the easiest way to start local development with all the major Saleor services:
- [Core GraphQL API](https://github.com/saleor/saleor)
- [Dashboard](https://github.com/saleor/saleor-dashboard)
- Mailpit (Test email interface)
- Jaeger (APM)
- The necessary databases, cache, etc.

*Keep in mind this repository is for local development only and is not meant to be deployed in any production environment! If you're not a developer and just want to try out Saleor you can check our [live demo](https://demo.saleor.io/).*

## Requirements
1. [Docker](https://docs.docker.com/install/)

## How to clone the repository?

To clone the repository, run the following command

```
git clone https://github.com/saleor/saleor-platform.git
```

## How to run it?

1. We are using shared folders to enable live code reloading. Without this, Docker Compose will not start:
    - Windows/MacOS: Add the cloned `saleor-platform` directory to Docker shared directories (Preferences -> Resources -> File sharing).
    - Windows/MacOS: Make sure that in Docker preferences you have dedicated at least 5 GB of memory (Preferences -> Resources -> Advanced).
    - Linux: No action is required, sharing is already enabled and memory for the Docker engine is not limited.

2. Go to the cloned directory:
```shell
cd saleor-platform
```

3. Build the application:
```shell
docker compose build
```

4. Apply Django migrations:
```shell
docker compose run --rm api python3 manage.py migrate
```

5. Populate the database with example data and create the admin user:
```shell
docker compose run --rm api python3 manage.py populatedb --createsuperuser
```
*Note that `--createsuperuser` argument creates an admin account for `admin@example.com` with the password set to `admin`.*

6. Run the application:
```shell
docker compose up
```

## Where is the application running?
- Saleor Core (API) - http://localhost:8000
- Saleor Dashboard - http://localhost:9000
- Jaeger UI (APM) - http://localhost:16686
- Mailpit (Test email interface) - http://localhost:8025
