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

   <img src="" width=800 />
   
3. Configure the cluster by specifying the node pool name, data center region, cluster capacity, and adding three nodes.
   
   <img src="" width=800 />
   
5. In the Overview section of the cluster configuration, download the cluster configuration file.
   
   <img src="" width=800 />
   
7. Update the file permissions to read-only.

   ```bash
   
   ```
   
   <img src="" width=800 />
   
9. Set the KUBECONFIG environment variable to the path of the configuration file.
    
   ```bash
   
   ```
   
   <img src="" width=800 />
   
11. Verify that the nodes are active

    ```bash
    
    ```

    <img src="" width=800 />

## Deploying replicated MongoDB in DigitalOcean using Helm charts and enabling data Persistence. 
1. Add the Bitnami Helm repository:
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
2. Search the Bitnami repository for available charts:
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
3. Search for the MongoDB chart:
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
4. Create a helm-mongodb.yaml file to override default values (e.g., architecture type, replica count, persistence settings, and authentication).
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
5. Install the MongoDB chart using your custom values:
      
   ```bash
   
   ```
   
   <img src="" width=800 />
   
6. Verify that the MongoDB pods are running and three replicas are active:
      
   ```bash
   
   ```
   
   <img src="" width=800 />
   
7. Check all installed components:
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
8. Confirm that the MongoDB secret was created:
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
9. Verify that persistent volumes were created in DigitalOcean.
      
   ```bash
   
   ```
   
   <img src="" width=800 />
   

## Deploying Mongo-Express
1. Deploy Mongo-Express using a YAML configuration similar to the previous demo.
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
2. Verify that the Mongo-Express pod is running.
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
3. Check the Mongo-Express logs to ensure it connected to MongoDB.
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   


## Deploying and Configuring Ingress to access Mongo-Express via WebUI
1. Add the ingress-nginx repository:
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
2. Install the ingress controller and enable automatic public IP allocation:
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
3. Verify that the ingress LoadBalancer was created in DigitalOcean.
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
4. Ensure the ingress controller pod is running.
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   
5. Configure routing rules in the ingress.yaml file. Note that the host field only accepts domain names—not IP addresses.

    <details><summary><strong> 💡 Tip: No Domain Name Available  </strong></summary>
     Because DigitalOcean does not provide a default domain name, you must use a fake hostname to complete the ingress.yaml file. Update your /etc/hosts file to map the LoadBalancer IP to a fake domain:
      ```bash
         vim /etc/hosts
         165.227.253.30 mongo.local
      ```
  </details>

   ```
   
   <img src="" width=800 />
   
  6. Apply the ingress.yaml file:
     
   ```bash
   
   ```
   
   <img src="" width=800 />
   

  7. Verify that the ingress resource is active:
     
     ```bash

     ```
   
   <img src="" width=800 />
   
  9. Access Mongo-Express in a web browser using the fake host (e.g., http://mongo.local)
     
     ```bash

     ```
   
   <img src="" width=800 />
   
  10. Add a new database and collection. Verify that the changes persist due to the enabled volume storage in DigitalOcean.

     ```bash

     ```
   
   <img src="" width=800 />
   
  
  
  
  
