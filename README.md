# *** Pod ***
- To create the Pod from your YAML file:    ```kubectl create -f pod-definition.yml```
- To list all Pods in your cluster:  kubectl get pods
- To view detailed information about the Pod:  kubectl describe pod <pod-name>
- To delete a pod:   kubectl delete pod <pod-name>

# *** Replication Controller ***
- To create the Replication Controller:  kubectl create -f rc-definition.yml
- To verify rs has been cretaed:   kubectl get replicationcontroller
- To view the pods managed by the replication controller:  kubectl get pods
- To delete Replication Controller:   kubectl delete replicationcontroller <replicationcontroller-name>

# *** ReplicaSet ***
- To create the ReplicaSet:   kubectl create -f replicaset-definition.yml
- To verify the creation of your ReplicaSet:   kubectl get replicaset
- To view the pods managed by the replicaset:   kubectl get pods
- To delete ReplicaSet:   kubectl delete rs <replicaset-name>

## Scaling a ReplicaSet:
- To update the replicas number in the definition file and apply the change: 
         kubectl replace -f replicaset-definition.yml
         kubectl apply -f replicaset-definition.yml

- 'kubectl scale' command can also be used to specify the new replica count using either the file or the ReplicaSet name:
        kubectl scale --replicas=5 -f replicaset-definition.yml
                              (or)
        kubectl scale --replicas=6 replicaset myapp-replicaset
