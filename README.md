# ☸️ Kubernetes
## 📦 Demo 3: Deploy MongoDb
This demo project is part of **Kubernetes Module** from Nana DevOps Bootcamp. It demonstrates how to deploy **MongoDB** on a **Kubernetes cluster hosted on DigitalOcean**, using **Helm** for package management and deployment.

## 🚀 Technologies Used
- **Kubernetes (minikube)**: Container orchestration
- **Digital Ocean**: Cloud Provider and Kubernetes Cluster
- **MongoDB**: noSQL Database.
- **Mongo-Express**: MongoDB UI 
  
## 📋 Prerequisites
- Ensure minikube is running
- Ensure you have the Digital Ocean account.
- Ensure Helm is installed on your machine.

## 🎯 Features

- Create a managed K8 cluster with Digital Ocean Kubernetes Engine.
- Deploy a replicated MongoDB service in a Digital Ocean Kubernetes cluster using a Helm chart.
- Configure Datapersistence for MongoDB with Digital Ocean's Cloud storage.
- Deploy UI Mongo-Express for MongoDB.
- Deploy and configure Nginx Ingress to access the UI application from a browser. 

## 🏗 Project Architecture

<img src=""/>

## ⚙️ Project Configuration

## Creating a managed K8 cluster using DigitalOcean Kubernetes Engine.
1. Go to Digital Ocean and Create a Kubernetes Cluster.
2. Configure the K8 cluster by providing the name of the pool, datacenter, selecting the cluster capacity, and adding three nodes.
3. Navigate to the cluster configuration and under the overview section download the Cluster configuration file.
4. Change the permission to the configuration file to only give read access.
5. Assign the file to the KUBECONFIG environment variable
6. Verify the nodes

## Deploying replicated MongoDB in DigitalOcean using Helm charts and configuring data persistence. 
1. Add the Bitnami repository to he cluster.
2. Search in the Bitnami repository for the available charts.
3. Search the MongoDB charts.
4. Create the helm-mongodb.yaml to override the values from the chart. We set the architecture type, number of replicas, persistence configuration, and authentication.
5. Install the MongoDB chart passing our configuration values.
6. Verify the running pods and check that the three MongoDB replicas are running.
7. Verify all the components installed.
8. Verify that the secret was created.
9. Verify that the Volumes were created in DigitalOcean to persist data.

## Deploying Mongo-Express
1. Apply the Mongo-Express deployment similar to the previous demo.
2. Verify that the Mongo-Express pod is running.
3. Verify the Mongo-Express logs.


## Deploying and Configuring Ingress to access Mongo-Express via WebUI
1. Add the ingress-nginx repository to the cluster.
2. Install the ingress controller and automatically pass the attribute to allocate a public IP.
3. Verify that the ingress Load Balancer was created in Digital Ocean
4. Verify that the ingress controller is running.
5. Configuring rules to route traffic to our host domain.

    <details><summary><strong> 💡 No host name available  </strong></summary>
     As we are using Digital Ocean, this cloud provider does not provide a hostname; therefore, we must use a fake host to complete the ingress.yaml file.
     To do this, modify the /etc/hosts using vim editor and add the mapping between the public ip address and the fake host as follows:
     ```bash
     vim /etc/hosts
  
     165.227.253.30 mongo.local
     ```
  </details>
