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

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/1%20creating%20k8%20digitalocean.png" width=800 />
   
2. Configure the cluster by specifying the node pool name, data center region, cluster capacity, and adding three nodes.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/2%20cluster%20capacity%20digitalocean%20workers%20nods.png" width=800 />
   
3. In the Overview section of the cluster configuration, download the cluster configuration file.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/3%20overview%20download%20config.png" width=800 />
   
4. Update the file permissions to read-only.

   ```bash
   chmod 400 k8s-1-32-2-do-1-nyc1-1746734593185-kubeconfig.yaml
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/4%20setting%20read%20only%20rights.png" width=800 />
   
5. Set the KUBECONFIG environment variable to the path of the configuration file.
    
   ```bash
   export KUBECONFIG=k8s-1-32-2-do-1-nyc1-1746734593185-kubeconfig.yaml   
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/5%20setting%20kubeconfig%20to%20the%20file.png" width=800 />
   
6. Verify that the nodes are active

    ```bash
    kubectl get node
    ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/6%20checking%20nodes.png" width=800 />

## Deploying replicated MongoDB in DigitalOcean using Helm charts and enabling data Persistence. 
1. Add the Bitnami Helm repository:
     
   ```bash
   helm repo add bitnami https://charts.bitnami.com/bitnami
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/7%20adding%20repo.png" width=800 />
   
2. Search the Bitnami repository for available charts:
     
   ```bash
   helm search repo bitnami
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/8%20see%20all%20charts%20available%20in%20the%20repo.png" width=800 />
   
3. Search for the MongoDB chart:
     
   ```bash
   helm search repo bitnami/mongodb
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/9%20to%20search%20for%20a%20specific%20chart.png" width=800 />
   
4. Create a helm-mongodb.yaml file to override default values (e.g., architecture type, replica count, persistence settings, and authentication).
     
   ```bash
   
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/10%20Helm%20mongodb%20to%20override%20chart%20parameters.PNG" width=800 />
   
5. Install the MongoDB chart using your custom values:
      
   ```bash
   helm install mongodb --values helm-demo/helm-mongodb.yaml bitnami/mongodb
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/11%20installing%20mongodb%20charts%20in%20the%20K8%20cluster.png" width=800 />
   
6. Verify that the MongoDB pods are running and three replicas are active:
      
   ```bash
   kubectl get pod
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/12%20mongodb%20pods%20running.png" width=800 />
   
7. Check all installed components:
     
   ```bash
   kubectl get all
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/13%20checking%20what%20has%20been%20created.png" width=800 />
   
8. Confirm that the MongoDB secret was created:
     
   ```bash
   kubectl get secret
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/14%20secret%20available.png" width=800 />
   
9. Verify that persistent volumes were created in DigitalOcean.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/15%20volumes%20created%20on%20DO%20persistent.png" width=800 />
   

## Deploying Mongo-Express
1. Deploy Mongo-Express using a YAML configuration similar to the previous demo.
     
   ```bash
   kubectl apply -f helm-demo/helm-mongo-express.yaml
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/17%20creating%20mongo%20express%20deployment%20and%20service.png" width=800 />
   
2. Verify that the Mongo-Express pod is running.
     
   ```bash
   kubectl get pod   
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/18%20checking%20mongo%20express%20pod.png" width=800 />
   
3. Check the Mongo-Express logs to ensure it connected to MongoDB.
     
   ```bash
   kubectl logs mongo-express-58cb4696d6-9qjv5
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/19%20checking%20mongo%20express%20logs.png" width=800 />
   


## Deploying and Configuring Ingress to access Mongo-Express via WebUI
1. Add the ingress-nginx repository:
     
   ```bash
   helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/20%20adding%20repository%20ingress.png" width=800 />
   
2. Install the ingress controller and enable automatic public IP allocation:
     
   ```bash
   helm install nginx-ingress ingress-nginx/ingress-nginx --set controller.publishService.enabled=true
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/21%20installing%20ingress%20passing%20attribute%20to%20automatically%20allocated%20an%20ip.png" width=800 />
   
3. Verify that the ingress LoadBalancer was created in DigitalOcean.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/23%20loadbalancer%20on%20DO.PNG" width=800 />
   
4. Ensure the ingress controller pod is running.
     
   ```bash
   kubecyl get pod   
   ```
   
   <img src=""https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/24%20pods.png width=800 />
   
5. Configure routing rules in the ingress.yaml file. Note that the host field only accepts domain names—not IP addresses.

    <details><summary><strong> 💡 Tip: No Domain Name Available  </strong></summary>
     Because DigitalOcean does not provide a default domain name, you must use a fake hostname to complete the ingress.yaml file. Update your /etc/hosts file to map the LoadBalancer IP to a fake domain:
      
      ```bash
           vim /etc/hosts
        ```
      ```bash
       165.227.253.30 mongo.local
      ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/25%20eidting%20the%20file%20to%20add%20the%20fake%20hostname.png" width=800 />
  
  </details>
  
  <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/26%20using%20the%20fake%20host%20just%20mapped.png" width=800 />
   
  6. Apply the ingress.yaml file:
     
   ```bash
    kubectl apply -f helm-demo/helm-ingress.yaml
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/27%20creating%20ingress.png" width=800 />
   

  7. Verify that the ingress resource is active:
     
     ```bash
     kubectl get ingress
     ```

     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/28%20checking%20ingress.png" width=800 />
   
  8. Access Mongo-Express in a web browser using the fake host (e.g., http://mongo.local)

     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/29%20mongo%20express%20access%20via%20ingress%20config.png" width=800 />
   
  9. Add a new database and collection. Verify that the changes persist due to the enabled volume storage in DigitalOcean.

      <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/30%20mongo%20express%20with%20db%20persisten%20bcd%20volumes.png" width=800 />
   
  
  10. Scale down the k8 cluster
      
      ```bash
      kubectl scale --replicas=0 statefulset/mongodb
      Kubetcl get pod      
      ```
      <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/31%20scaling%20down.png" width=800 />
      
  11. Scale up the k8 cluster.

      ```bash
      kubectl scale --replicas=3 statefulset/mongodb
      kubectl get pod
      ```
      <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/32%20scale%20up.png" width=800 />
      
  12. Uninstall MongoDB and its components. 

      ```bash
      helm uninstall mongodb
      ```
      <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_DO_MongoDB/blob/main/Img/34%20uninstalling%20mongo%20db%20with%20associated%20%20config.png" width=800 />
  
  
