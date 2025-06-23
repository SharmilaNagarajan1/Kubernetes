# Kubernetes
Kubernetes (commonly referred to as "K8s") is an open source system for automating deployment, scaling and management of containerized applications originally designed by Google and donated to the Cloud Native Computing Foundation. It aims to provide a "platform for automating deployment, scaling, and operations of application containers across clusters of hosts". It supports a range of container tools, including Docker.


# <strong>Pod</strong> - The smallest deployable unit in Kubernetes that runs one or more containers.
- To create the Pod from your YAML file:    ```kubectl create -f pod-definition.yml```
- To list all Pods in your cluster:  ```kubectl get pods```
- To view detailed information about the Pod:  ```kubectl describe pod <pod-name>```
- To delete a pod:   ```kubectl delete pod <pod-name>```

# <strong>Replication Controller</strong> - Ensures a specified number of identical pods are running at all times (legacy feature).
- To create the Replication Controller:  ```kubectl create -f rc-definition.yml```
- To verify rs has been cretaed:   ```kubectl get replicationcontroller```
- To view the pods managed by the replication controller:  ```kubectl get pods```
- To delete Replication Controller:   ```kubectl delete replicationcontroller <replicationcontroller-name>```

# </strong>ReplicaSet</strong> - A newer controller that maintains a stable set of replica pods, replacing ReplicationController.
- To create the ReplicaSet:   ```kubectl create -f replicaset-definition.yml```
- To verify the creation of your ReplicaSet:   ```kubectl get replicaset```
- To view the pods managed by the replicaset:   ```kubectl get pods```
- To delete ReplicaSet:   ```kubectl delete rs <replicaset-name>```

## Scaling a ReplicaSet:
- To update the replicas number in the definition file and apply the change: 
         ```kubectl replace -f replicaset-definition.yml```
         ```kubectl apply -f replicaset-definition.yml```

- 'kubectl scale' command can also be used to specify the new replica count using either the file or the ReplicaSet name:
        ```kubectl scale --replicas=5 -f replicaset-definition.yml```
                              (or)
        ```kubectl scale --replicas=6 replicaset myapp-replicaset```
# </strong>Deployment</strong> - Manages ReplicaSets and provides features like rolling updates and rollback for pod updates.
- To create the deployment from your YAML file:  ```kubectl create -f deployment.yaml```
- To list deployments:  ``` kubectl get deployments```
- To inspect the pods created by the deployment:   ```kubectl get pods```
- To view detailed information about the deployment:   ```kubectl describe deployment <deployment-name>```
- To list all objects created in the cluster:  ```kubectl get all```
