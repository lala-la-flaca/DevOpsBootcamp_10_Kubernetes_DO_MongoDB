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

## Creating a Managed K8 Cluster using DigitalOcean Kubernetes Engine.
1. Sign in to DigitalOcean and create a Kubernetes cluster.
2. Configure the cluster by specifying the node pool name, data center region, cluster capacity, and adding three nodes.
3. In the Overview section of the cluster configuration, download the cluster configuration file.
4. Update the file permissions to read-only.
5. Set the KUBECONFIG environment variable to the path of the configuration file.
6. Verify that the nodes are active

## Deploying replicated MongoDB in DigitalOcean using Helm charts and enabling data Persistence. 
1. Add the Bitnami Helm repository:
2. Search the Bitnami repository for available charts:
3. Search for the MongoDB chart:
4. Create a helm-mongodb.yaml file to override default values (e.g., architecture type, replica count, persistence settings, and authentication).
5. Install the MongoDB chart using your custom values:
6. Verify that the MongoDB pods are running and three replicas are active:
7. Check all installed components:
8. Confirm that the MongoDB secret was created:.
9. Verify that persistent volumes were created in DigitalOcean.

## Deploying Mongo-Express
1. Deploy Mongo-Express using a YAML configuration similar to the previous demo.
2. Verify that the Mongo-Express pod is running.
3. Check the Mongo-Express logs to ensure it connected to MongoDB.


## Deploying and Configuring Ingress to access Mongo-Express via WebUI
1. Add the ingress-nginx repository:
2. Install the ingress controller and enable automatic public IP allocation:
3. Verify that the ingress LoadBalancer was created in DigitalOcean.
4. Ensure the ingress controller pod is running.
5. Configure routing rules in the ingress.yaml file. Note that the host field only accepts domain names—not IP addresses.

    <details><summary><strong> 💡 Tip: No Domain Name Available  </strong></summary>
     Because DigitalOcean does not provide a default domain name, you must use a fake hostname to complete the ingress.yaml file. Update your /etc/hosts file to map the LoadBalancer IP to a fake domain:
      ```bash
         vim /etc/hosts
         165.227.253.30 mongo.local
      ```
  </details>
  6. Apply the ingress.yaml file:
  7. Verify that the ingress resource is active:
  8. Access Mongo-Express in a web browser using the fake host (e.g., http://mongo.local)
  9. Add a new database and collection. Verify that the changes persist due to enabled volume storage in DigitalOcean.
  
  
  
  
