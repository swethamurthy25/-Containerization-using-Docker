# Containerization-using-Docker

### The intended function of web-based service in Docker:

Docker is open-source software for creating, deploying, and managing virtualized application containers on several operating systems. The main purpose of docker is to package all your environmental variables into a docker image. This simplifies the setup of different environments with the same configuration. So, developers can quickly create their working environment with Docker, maintain it up to date, and ensure that it is identical to the production environment.

Though the overall infrastructure of local development, staging, and production environments may differ, the core components are the same containers with the same configurations. For building and storing docker images, Docker Hub is used because it supports the automated building of images whenever the docker file changes. We just need to update the docker image and run a container with the updated version to make the changes. Also using web-based services in docker helps to eliminate the difference in the configuration of development, staging, and production environments. It helps to eliminate long and painful deployments on production servers. It simplifies the process of changing the environment configuration and replicating the server in case of failure.

### Process Used to build the Docker:

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

#### Step 3:
I have used the below four files to build the container. This can be done by using the vi editor and with the below command:

* Create file – “vim <filename>”
* View file – “vi <filename
* Files: requirements.txt, main.py, dockerfile and docker-compose.yml

#### Step 4:
Then we need to build the docker image and it can be viewed as well.  
* Command to build docker image - “sudo docker build .“
* Command to view the image that has been built in the previous step - “sudo docker images”

![image](https://github.com/swethamurthy25/-Containerization-using-Docker/assets/112581595/d9fd19f2-b5e9-49a9-ba46-91e1e4045e16)

#### Step 5:
* Additionally, I have also created a compose file (docker-compose.yml) to execute the Webservice.
* Now when we execute the command, “sudo docker-compose up” it will run our web services with the IP address and port numbers.
* In our case, the IP Address is https://172.19.0.2:5000/ , and 172 is automatically allocated for docker.

![image](https://github.com/swethamurthy25/-Containerization-using-Docker/assets/112581595/07f3eb6b-9bdc-4da7-858d-2959c96a595a)


### Hardware Utilization and Implications in Docker Containerization

Docker is built on a client-server architecture. The Docker client communicates with the Docker daemon, which handles the construction, execution, and distribution of the Docker containers. We can execute the Docker client and daemon on the same machine, or we can link a Docker client to a Docker daemon that is located elsewhere. The Docker client communicates with the daemon using a REST API, over UNIX sockets or a network interface. We also have another Docker client called Docker Compose, which lets us work with applications consisting of a set of containers. 

#### Docker Deamon:

When we use docker, we are creating and using images, containers, networks, volumes, plugins, and other objects. These docker objects are managed by the Docker daemon (dockerd), which listens for Docker API calls and handles them.

#### Docker Client:

The Docker client is the primary way that is used to interact with Docker. 

#### Docker Registries:

A registry is used to store Docker images and Docker Hub is a public registry that anyone can access. When we use the docker run or docker pull command, the required images are pulled from the configured registry.

#### Docker Image:

To build our own image, we must create a docker file with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers that have changed are rebuilt.

With respect to security, docker containers are very similar to LXC containers, and they have similar security features. Container namespaces provide users with their own perspective of the underlying Linux system, limiting what they can see and do. When you run a container, Docker creates namespaces that the specific container will use. We also have Control groups which are Linux kernel features that isolate, prioritize, and account for a set of processes' resource utilization (CPU, memory, disk I/O, network, and so on).


### Exploring Operating Systems and Service Containerization Interactions

Application delivery requires special attention in today's software environment when the majority of jobs are executed in the cloud and in a DevOps culture, to keep the business running. Cloud and virtualization are tools for improving server efficiency and utilizing server resources as part of the infrastructure streamlining process. That's where containerization technology came into play. Containerization emerged as a sophisticated method for maximizing server efficiency while requiring few new resources. A Docker container is a method of packing a Linux application, including all its libraries, data files, and environment variables, to ensure that the execution environment is uniform across all Linux systems and instances on the same host. All the kernel calls from the container are handled by the host system kernel. To run several containers on the same OS, Docker uses resource isolation in the OS kernel.  Virtual machines (VMs), on the other hand, enclose a whole operating system with executable code on top of an abstracted layer of physical hardware resources. 

DGXTM systems use Docker containers to install deep learning frameworks. A virtual machine duplicates all the components of a real computer, including the screen and the hard disk, which on a real computer (also known as the host) is just a single large file (called a virtual hard drive). Docker virtualizes a host operating system in the same way that VirtualBox does. Docker containers are great for quickly spinning up and scraping apps in a separate environment, but because they are virtual machines, they require a permanent storage mechanism. Docker volumes are made specifically for this purpose. We can create and erase hard drive storage simulations in seconds, and mount, read, write, and eject them from containers with ease.

### Implementation & Source Code

File – main.py

```python
from flask import Flask
app = Flask(_name_)
@app.route('/')
def swetha():
        return '<body style="background-color:powderblue;"><h2>Welcome to IFT510-Project by Swetha</h2></body>'
@app.route('/next')
def swetha1():
        return '<body style="background-color:tomato;"><h2> Publishing the docker container to GITHUB</h2> </body>'
if _name_ == '_main_':	
	app.run(host="0.0.0.0", debug=True)
```

Docker file

```python
FROM scratch
ADD alpine-minirootfs-3.11.8-x86_64.tar.gz /
RUN /bin/sh
EXPOSE 5000
RUN apk add --update python3 python3-dev py3-pip build-base
COPY . /app
WORKDIR /app
RUN pip3 install --no-cache-dir -r requirements.txt
ENTRYPOINT [ "python3" ]
CMD ["main.py"]
```

Requirements.txt

Flask==2.0.3

docker-compose.yml (Flask+Python)
```python
version: "2.2"
services:
  app:
    build: .
    command: python main.py
    ports:
      - "5000:5000"
    volumes:
      - .:/python-flask
```


### Evidence of Working:

![image](https://github.com/swethamurthy25/-Containerization-using-Docker/assets/112581595/bff1fffd-fed9-4d68-87f2-6282c1ca7bc0)

When we execute the command sudo docker run <image_id> , it runs in the IP Address and port: http://172.17.0.2:5000/

![image](https://github.com/swethamurthy25/-Containerization-using-Docker/assets/112581595/f016f257-dac8-4ad9-bdd6-260fdb35b613)




