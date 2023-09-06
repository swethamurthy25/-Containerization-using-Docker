# Containerization-using-Docker

### The intended function of web-based service in Docker:

Docker is open-source software for creating, deploying, and managing virtualized application containers on several operating systems. The main purpose of docker is to package all your environmental variables into a docker image. This simplifies the setup of different environments with the same configuration. So, developers can quickly create their working environment with Docker, maintain it up to date, and ensure that it is identical to the production environment.

Though the overall infrastructure of local development, staging, and production environments may differ, the core components are the same containers with the same configurations. For building and storing docker images, Docker Hub is used because it supports the automated building of images whenever the docker file changes. We just need to update the docker image and run a container with the updated version to make the changes. Also using web-based services in docker helps to eliminate the difference in the configuration of development, staging, and production environments. It helps to eliminate long and painful deployments on production servers. It simplifies the process of changing the environment configuration and replicating the server in case of failure.

### Implementation Procedure:

#### Step 1:
Set up the virtual environment to run the docker. For this project, I have used the below packages:
  
* Oracle Virtual Box – 6.1.22 platform packages
* Ubuntu Desktop – 20.04 LTS
* Python – 3.8.10
* Flask – 2.0.3

#### Step 2:
A directory must be created to run the docker file. This can be done using the command: Here, I have created the directory called Docker

* Directory creation – “mkdir <directory_name>”
* View the created directory – “cd <directory_name>”

