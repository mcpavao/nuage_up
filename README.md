# Application on Docker / Kubernetes
Containerizing and Deploying our Application on Docker and Kubernetes. 
The main goal of this repository is for study and assesments. 
If you have any questions, please do not hesitate to contact me.

# Pre-requisites 
Before you start, please make sure you have all the dependencies installed.
- Docker (https://docs.docker.com/engine/install/)
- Access to DockerHub
- Kubernetes (https://kubernetes.io/docs/setup/)
- Kubectl: Kubenetes Command Line Tool (https://kubernetes.io/docs/tasks/tools/)
- KIND: Tool to generate and manager the cluster - the same link as above.
- Jenkins: CD/CI Automation Tool (https://www.jenkins.io/doc/book/installing/)

# Steps
Once you have all the pre-requisites installed, please follow below:

1 - Download the Dockerimage from the DockerHub Repository:
- docker pull mcpavaopereira/nuage_test:latest
  
2 - Download the Github files from my GitHub repository:
- Deployment.yaml
- Service.yaml
- Ingress.yaml
- hpa.yaml
- networkpolicy.yaml

# Testing the DockerImage 

Make sure the Docker status is active:

If you are a Linux user, you can run 
sudo systemctl status docker 

If you see the status : active(running), you are ready to procced

You can test the Docker Image running locally using: 
- docker run -p 80:80 mcpavaopereira/nuage_test:latest

When you open you browser and type http://localhost - The nuage_up app will appear
Once you tested the image, you can stop the process:
    docker stop <container_name>

# Innitializing the App via K8s(Kubernetes)

