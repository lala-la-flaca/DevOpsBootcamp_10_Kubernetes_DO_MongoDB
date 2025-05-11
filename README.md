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
- Deploy a replicated MongoDB service in Digital Ocean Kubernetes cluster using Helm chart.
- Configure Datapersistence for MongoDB with Digital Ocean's Cloud storage.
- Deploy UI Mongo-Express for MongoDB.
- Deploy and configure Nginx Ingress to access the UI application from a browser. 

## 🏗 Project Architecture

<img src=""/>

## ⚙️ Project Configuration

## Creating a managed K8 cluster using DigitalOcean Kubernetes Engine.
1. Go to Digital Ocean and Create a Kubernetes Cluster.
2. Configure the K8 cluster by providing the name of the pool, datacenter, select the cluster capacity, and add three nodes.
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
1. Apply the Mongo-Express deployment similar to previous demo.
2. Verify that The Mongo-Express pod is running.
3. Verify thhe Mongo-Express logs.


## Deploying and Configuring Ingress to access Mongo-Express via WebUI
1. Add the ingress-nginx repository to the cluster.
2. Install the ingress controller and pass the attribute to allocate a public IP automatically.
3. Verify that the ingress controller is running.
4. Configuring rules to route traffic to our host domain.
   No Doi

