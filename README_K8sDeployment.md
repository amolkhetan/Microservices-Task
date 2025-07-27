# Microservices Kubernetes Deployment
This repository contains a nodejs applications having user, product and order services connected via gateway service.Below is the port configuration:

User Service (Port 3000)
Product Service (Port 3001)
Order Service (Port 3002)
Gateway Service (Port 3003)

---

## 🛠️ Tech Stack

- **nodejs** – App codinging language
- **Docker** – Building Docker Image
- **K8s/Minikube** – For Deployment

---


## Docker Images were built using Dockerfile in root path of each service's folder.

docker build -t amolkhetan/micro-services_user-service . 
docker build -t amolkhetan/micro-services_product-service . 
docker build -t amolkhetan/micro-services_order-service . 
docker build -t amolkhetan/micro-services_gateway-service . 

Push Command
docker push amolkhetan/micro-services_user-service:latest
docker push amolkhetan/micro-services_product-service:latest
docker push amolkhetan/micro-services_order-service:latest
docker push amolkhetan/micro-services_gateway-service:latest


## K8s deployment files
Deployment.yaml and Service.yaml has been created for all the services and kept in k8s/deployments and k8s/services folder of the repo.

## MiniKube Install
Now, we have k8s file ready.  We can use K8s cluster from docker-desktop or install minikube.
Here, we will install minikube and deploy application on it.

It can be installed using either of the below command depening on what you have scoop or choclatey

choco install minikube
     or
scoop install minikube

<img width="940" height="173" alt="image" src="https://github.com/user-attachments/assets/afea010b-6834-4556-8618-e1177462609e" />

check minikube version

<img width="940" height="203" alt="image" src="https://github.com/user-attachments/assets/dd8f3ab3-0758-4a93-891b-d2be565250b7" />

## Deploy Application on Minikube
Start minikube using

minikube start --driver=docker

<img width="1469" height="434" alt="image" src="https://github.com/user-attachments/assets/81f00f96-69a8-4979-bc78-2fbd5962d647" />

Deploy App using kubectl apply 

<img width="1480" height="270" alt="image" src="https://github.com/user-attachments/assets/e157d9b8-7716-41e5-8d6f-f46bc07e0c7e" />

Verify the deployments
<img width="1479" height="338" alt="image" src="https://github.com/user-attachments/assets/64ea0607-cd66-4fe2-8408-309617f2d0bd" />

## Testing
Since we have used ClusterIP for all services, they can't be tested from outside network directly.
We can test using port forward like below and use local host on ports used to access url.

User-Service
<img width="1472" height="102" alt="image" src="https://github.com/user-attachments/assets/859dd353-f5c8-467d-8a5f-1a83a03236e5" />

<img width="1909" height="175" alt="image" src="https://github.com/user-attachments/assets/805b3efc-3bfe-4753-9771-e67eefe46b4b" />

Product-Service
<img width="1477" height="130" alt="image" src="https://github.com/user-attachments/assets/f75d7d5e-8b8a-4f65-9353-eb1b9157e5ec" />

<img width="1914" height="160" alt="image" src="https://github.com/user-attachments/assets/b4965324-a2a9-48e5-9270-ae47e8bcc519" />

Order-Service
<img width="1483" height="87" alt="image" src="https://github.com/user-attachments/assets/d7422be5-b1e3-4f33-975e-ced97a58e27c" />

<img width="1919" height="182" alt="image" src="https://github.com/user-attachments/assets/f9a95466-fb5f-472c-b418-81a6aac3b9bf" />

Gateway-Service
<img width="1471" height="122" alt="image" src="https://github.com/user-attachments/assets/b1d3eb57-1b0d-4062-8613-d9c28e4259ca" />

<img width="1914" height="147" alt="image" src="https://github.com/user-attachments/assets/87c5334a-505e-446e-91d0-95594ec0d1b4" />
<img width="1915" height="167" alt="image" src="https://github.com/user-attachments/assets/c5a071f2-444e-40d6-8468-08edc2b5b65a" />
<img width="1913" height="117" alt="image" src="https://github.com/user-attachments/assets/8b332801-a9b1-43f8-b0cc-0563d59c9333" />

Server Communication logs
<img width="1474" height="374" alt="image" src="https://github.com/user-attachments/assets/482a8a32-0782-4ab4-93de-b54b21a4ed6f" />


## Ingress
Install ingress using below command

<img width="1484" height="252" alt="image" src="https://github.com/user-attachments/assets/89725389-e7dc-4931-b014-809112c093b6" />

Run below command to apply ingress in cluster:
kubectl apply -f .\k8s\ingress\ingress.yaml (file is present in repo)

<img width="1438" height="165" alt="image" src="https://github.com/user-attachments/assets/c1559300-5d58-44ba-8f57-fbfe43778a37" />

now add IP address and DNS in /etc/hosts

Ingress is not working as expected, debugging in progress

<img width="1381" height="200" alt="image" src="https://github.com/user-attachments/assets/60028af6-7b11-4c86-97bb-e481fcb96ff4" />









