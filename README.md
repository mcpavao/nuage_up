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

1 - Create a Cluster via KIND(Kubernetes) using the command below:
In your terminal run the command: - kind create cluster

 To check if the cluster has been created, please run:
- kubectl get nodes

The cluster name and details will appear

# Applying yaml files to have the application running in you cluster

Start with the command below:

- kubectl apply -f deployment.yaml
- kubectl apply -f service.yaml
- kubectl apply -f ingress.yaml
- kubectl apply -f hpa.yaml
- kubectl apply -f networkpolicy.yaml

Once you have those files applied into your node(cluster) we can test it.

# Testing Tools
- Deployment
  - kubectl get deployments

    This command will display the number of pods ready(in service) availability and age(when it was created)

- Service
  - kubectl get services

    This command will display the service name, type of service, cluster-ip, external-ip, ports and age.
    In our case, the type of service is LoadBalancer. If you deploy this application on AWS(for example) and you Elastic LoadBalancer is configured
    an external IP will be allocated for our application. Meaning, the application can be accessed externally.

  - In case to test locally, please change the service.yaml file removing the type of service field. After, run the command below
    - kubectl port-forward <svc/service-name> <port:port>

- Ingress
  - kubectl get ingress

This command will show the ingress name, hosts, address, ports and age.

- HPA
  - kubectl get hpa

This command will show the number of replicas, minimum pods and maximum pods. In case of CPU hits 70% of capacity, a new pod will be added.
 
- NetworkPolicy
  - kubectl get networkpolicy

The application is running, dockerized and containerized in Kubernetes.!!



