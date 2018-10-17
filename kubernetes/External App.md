# Exposing an External IP Address to Access an Application in a Cluster

[Original Tutorial](https://kubernetes.io/docs/tutorials/stateless-application/expose-external-ip-address/)

## Creating a service for an application running in five pods

1.  Run a Hello World application in your cluster:
    
        kubectl run hello-world --replicas=5 --labels="run=load-balancer-example" --image=jsaintrocc/arm32v6-hello-app:latest  --port=8080

2.  Wait for the pods to come up

        kubectl get pods
        >NAME                           READY     STATUS    RESTARTS   AGE
        >hello-world-664687dd5d-dssfx   1/1       Running   0          13m
        >hello-world-664687dd5d-kfd7p   1/1       Running   0          12m
        >hello-world-664687dd5d-l2wnl   1/1       Running   0          12m
        >hello-world-664687dd5d-r8b8x   1/1       Running   0          12m
        >hello-world-664687dd5d-zp45t   1/1       Running   0          12m

    Note: Yeah... takes a while on the pi's
    
3.  Display information about the Deployment:

        kubectl get deployments hello-world
        >NAME          DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
        >hello-world   5         5         5            5           1h
        kubectl describe deployments hello-world
        >Name:                   hello-world
        >Namespace:              default
        >CreationTimestamp:      Wed, 17 Oct 2018 04:25:42 +0000
        >Labels:                 run=load-balancer-example
        >Annotations:            deployment.kubernetes.io/revision=1
        >Selector:               run=load-balancer-example
        >Replicas:               5 desired | 5 updated | 5 total | 5 available | 0 unavailable
        >StrategyType:           RollingUpdate
        >MinReadySeconds:        0
        >RollingUpdateStrategy:  25% max unavailable, 25% max surge
        >Pod Template:
        >  Labels:  run=load-balancer-example
        >  Containers:
        >   hello-world:
        >    Image:        jsaintrocc/arm32v6-hello-app:latest
        >    Port:         8080/TCP
        >    Host Port:    0/TCP
        >    Environment:  <none>
        >    Mounts:       <none>
        >  Volumes:        <none>
        >Conditions:
        >  Type           Status  Reason
        >  ----           ------  ------
        >  Available      True    MinimumReplicasAvailable
        >  Progressing    True    NewReplicaSetAvailable
        >OldReplicaSets:  <none>
        >NewReplicaSet:   hello-world-664687dd5d (5/5 replicas created)
        >Events:          <none>

4.  Display information about your ReplicaSet objects:

        kubectl get replicasets
        >NAME                     DESIRED   CURRENT   READY     AGE
        >hello-world-664687dd5d   5         5         5         15m
        kubectl describe replicasets
        >Name:           hello-world-664687dd5d
        >Namespace:      default
        >Selector:       pod-template-hash=2202438818,run=load-balancer-example
        >Labels:         pod-template-hash=2202438818
        >                run=load-balancer-example
        >Annotations:    deployment.kubernetes.io/desired-replicas=5
        >                deployment.kubernetes.io/max-replicas=7
        >                deployment.kubernetes.io/revision=1
        >Controlled By:  Deployment/hello-world
        >Replicas:       5 current / 5 desired
        >Pods Status:    5 Running / 0 Waiting / 0 Succeeded / 0 Failed
        >Pod Template:
        >  Labels:  pod-template-hash=2202438818
        >           run=load-balancer-example
        >  Containers:
        >   hello-world:
        >    Image:        jsaintrocc/arm32v6-hello-app:latest
        >    Port:         8080/TCP
        >    Host Port:    0/TCP
        >    Environment:  <none>
        >    Mounts:       <none>
        >  Volumes:        <none>
        >Events:
        >  Type    Reason            Age   From                   Message
        >  ----    ------            ----  ----                   -------
        >  Normal  SuccessfulCreate  15m   replicaset-controller  Created pod: hello-world-664687dd5d-zp45t
    
5.  Create a Service object that exposes the deployment:

https://www.infralovers.com/en/articles/2017/04/22/kubernetes-and-traefik-on-raspberry/
https://blog.hypriot.com/post/setup-kubernetes-raspberry-pi-cluster/
https://docs.traefik.io/user-guide/kubernetes/
https://medium.com/@evnsio/managing-my-home-with-kubernetes-traefik-and-raspberry-pis-d0330effea9a

        kubectl expose deployment hello-world --type=Node --name=my-service
        kubectl expose deployment hello-world --type=LoadBalancer --name=my-service
        >service/my-service exposed 

6.  Display information about the Service:

        kubectl get services my-service
        >NAME         TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
        >my-service   LoadBalancer   10.111.90.169   <pending>     8080:31055/TCP   1m
    
    The output is similar to this:
    
    ```
    NAME         TYPE        CLUSTER-IP     EXTERNAL-IP      PORT(S)    AGE
    my-service   ClusterIP   10.3.245.137   104.198.205.71   8080/TCP   54s
    
    ```
    
    Note: If the external IP address is shown as <pending>, wait for a minute and enter the same command again.
    
7.  Display detailed information about the Service:
    
    ```
    kubectl describe services my-service
    
    ```
    
    The output is similar to this:
    
    ```
    Name:           my-service
    Namespace:      default
    Labels:         run=load-balancer-example
    Annotations:    <none>
    Selector:       run=load-balancer-example
    Type:           LoadBalancer
    IP:             10.3.245.137
    LoadBalancer Ingress:   104.198.205.71
    Port:           <unset> 8080/TCP
    NodePort:       <unset> 32377/TCP
    Endpoints:      10.0.0.6:8080,10.0.1.6:8080,10.0.1.7:8080 + 2 more...
    Session Affinity:   None
    Events:         <none>
    
    ```
    
    Make a note of the external IP address (`LoadBalancer Ingress`) exposed by your service. In this example, the external IP address is 104.198.205.71. Also note the value of  `Port`  and  `NodePort`. In this example, the  `Port`  is 8080 and the  `NodePort`  is 32377.
    
8.  In the preceding output, you can see that the service has several endpoints: 10.0.0.6:8080,10.0.1.6:8080,10.0.1.7:8080 + 2 more. These are internal addresses of the pods that are running the Hello World application. To verify these are pod addresses, enter this command:
    
    ```
    kubectl get pods --output=wide
    
    ```
    
    The output is similar to this:
    
    ```
    NAME                         ...  IP         NODE
    hello-world-2895499144-1jaz9 ...  10.0.1.6   gke-cluster-1-default-pool-e0b8d269-1afc
    hello-world-2895499144-2e5uh ...  10.0.1.8   gke-cluster-1-default-pool-e0b8d269-1afc
    hello-world-2895499144-9m4h1 ...  10.0.0.6   gke-cluster-1-default-pool-e0b8d269-5v7a
    hello-world-2895499144-o4z13 ...  10.0.1.7   gke-cluster-1-default-pool-e0b8d269-1afc
    hello-world-2895499144-segjf ...  10.0.2.5   gke-cluster-1-default-pool-e0b8d269-cpuc
    
    ```
    
9.  Use the external IP address (`LoadBalancer Ingress`) to access the Hello World application:
    
    ```
    curl http://<external-ip>:<port>
    
    ```
    
    where  `<external-ip>`  is the external IP address (`LoadBalancer Ingress`) of your Service, and  `<port>`  is the value of  `Port`  in your Service description. If you are using minikube, typing  `minikube service my-service`  will automatically open the Hello World application in a browser.
    
    The response to a successful request is a hello message:
    
    ```
    Hello Kubernetes!
    
    ```
    

## Cleaning up[](https://kubernetes.io/docs/tutorials/stateless-application/expose-external-ip-address/#cleaning-up)

To delete the Service, enter this command:

```
    kubectl delete services my-service

```

To delete the Deployment, the ReplicaSet, and the Pods that are running the Hello World application, enter this command:

```
    kubectl delete deployment hello-world

```

## What's next
http://www.pivpn.io/
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIxMzg5MTk3LDEzNTAxNTM4NjgsLTE3OT
A3MDUyOTEsMjE2MTUzNzYwLDkyOTQ2NjE5LDg5NTcyNjg0NCwt
MTEwMTQ2MzI1MywxNTI4MTczMDQ0LDIwMTYxNDg5MjYsODg1OD
U2Njk3LC0xNTYxMDg4MTMxXX0=
-->