1. Create a Pod with the the name “nginx-server” using a nginx image
    * Enlist all objects that were created with the pod such as services, depoyments, replicasets etc.
    * Delete the Pod
    * After deleting the Pod, verify whether the pod was deleted
    ###



##### Run a Pod with the name "nginx-server" using the nginx image

```
kubectl run nginx-server --image nginx
```



##### List all created Pods 

```
kubectl get pods
```

##### List most important information about ressources
```
kubectl get all
```

##### Cleaning up by deleteing ressources
```
kubectl delete deployment my-nginx
```


##### Verify what has been deleted
```
kubectl get all
```
___
      
2. Run a Deployment with one ReplicaSet using a httpd image with the name “my-apache-server”
    * Which objects were created  - how would you verify?
    * Scale the ReplicaSet to 3 replicas
    * Verify that three replicas are running
    * Verify that three pods are running
    * Show a contionous log of the Deployment with the name “my-apache-server” with 5 entries
    * Find out the Namespace in which the my-apache-server has been placed
    ###



##### Start a new Apache Webserver with the name "my-apache-server"


```
kubectl run my-apache-server --image httpd
```

##### Show the objects that have been deployed
```
kubectl get all
```

##### Scale the Replica Sets

```
kubectl scale deploy/my-apache-server --replicas 3

```

 * `kubectl scale deployment my-apache-server --replicas` 3 will do the same job



##### Verify that 2 Replicas are really running
```
kubectl get all
```
##### Display which pods are running
```
kubectl get pods
```


##### Show logs of a particular deployment
```
kubectl logs deployment/my-apache-server
```

##### Show the last 5 lines of a log continously
```
kubectl logs deployment/my-apache-server --follow --tail 5
```
##### Obtain the details of a specific ressource and Get the name of the Pod whose details are needed
```
kubectl get pods
```
##### Obtain required details
```
kubectl describe pod/my-apache-server-<pod id>
```

___

      



3. Open a second terminal and set up a constant watch on the pods
    * In the first terminal delete the pod
    * Use the second terminal to observe what happens when the pod is deleted


##### Monitor through the watch command in a second terminal
```
kubectl get pods -w
```


#### Delete a respective
```
kubectl delete pod/my-apache-<pod id>
```
#### Verify whether the pod has been deleted
```
kubectl get pods
```
___


4. Clean up your environment


##### Delete the Deployment


```
kubectl delete deployment my-apache-server
```

