# Deploying an App in AKS with LoadBalancer Service

This guide demonstrates how to deploy a simple Node.js application in Azure Kubernetes Service (AKS) and expose it using a LoadBalancer service.

---

## 1. Create a Namespace

```kubectl create namespace demo```

## 2. Create a deployment that runs your application pods called deployment.yml

## 3. Apply the deployment to your cluster by running the following command:

```kubectl apply -f deployment.yml```
```kubectl get pods -n demo -o wide```

But it’s not reachable from outside the cluster. That’s where a Load Balancer comes in.

## 4. Let’s define the load balancer service with a file called service.yaml.

## 5. Apply the service to your cluster by running the following command

```kubectl apply -f service.yml```

Within a minute, the load balancer should be confirmed up and running. Wait for the service to get an external IP address assigned by Azure.

## 6. You can check the status of the service by running the following command:

```kubectl get service```

## 7. Browse to external IP http://<ExternalIPOfService>
You should see your application is running 
