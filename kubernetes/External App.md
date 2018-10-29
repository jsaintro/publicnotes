# Exposing an External IP Address to Access an Application in a Cluster

[Original Tutorial](https://kubernetes.io/docs/tutorials/stateless-application/expose-external-ip-address/)

## Requirements
* rpi Kubernetes cluster
* Metallb-rpi (To simulate cloud LB)

## Creating a service for an application running in five pods

1.  Run a Hello World application in your cluster:
    
        kubectl create hello-world --replicas=5 --labels="run=load-balancer-example" --image=jsaintrocc/arm32v6-hello-app:latest  --port=8080

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

        kubectl expose deployment hello-world --type=LoadBalancer --name=my-service
        >service/my-service exposed 

6.  Display information about the Service:

        kubectl get services my-service
        >NAME         TYPE           CLUSTER-IP     EXTERNAL-IP      PORT(S)          AGE
        >my-service   LoadBalancer   10.98.13.135   192.168.86.101   8080:30674/TCP   20h
    
    Note: If EXTERNAL-IP is stuck in pending check to make sure you installed metallb correctly
    
7.  Display detailed information about the Service:
    
        kubectl describe services my-service
        >Name:                     my-service
        >Namespace:                default
        >Labels:                   run=load-balancer-example
        >Annotations:              <none>
        >Selector:                 run=load-balancer-example
        >Type:                     LoadBalancer
        >IP:                       10.98.13.135
        >LoadBalancer Ingress:     192.168.86.101
        >Port:                     <unset>  8080/TCP
        >TargetPort:               8080/TCP
        >NodePort:                 <unset>  30674/TCP
        >Endpoints:                10.38.0.12:8080,10.38.0.13:8080,10.38.0.14:8080 + 2 more...
        >Session Affinity:         None
        >External Traffic Policy:  Cluster
        >Events:                   <none>    
    
    Note of the external IP address (`LoadBalancer Ingress`) exposed by your service. In this example, the external IP address is 192.168.86.101. Also note the value of  `Port`  and  `NodePort`. In this example, the  `Port`  is 8080 and the  `NodePort`  is 30674.
    
8.  In the preceding output, you can see that the service has several endpoints: 10.38.0.12:8080,10.38.0.13:8080,10.38.0.14:8080 + 2 more. These are internal addresses of the pods that are running the Hello World application. To verify these are pod addresses, enter this command:
    
        kubectl get pods --output=wide
        >NAME                           READY     STATUS    RESTARTS   AGE       IP           NODE
        >hello-world-664687dd5d-8kq82   1/1       Running   0          3d        10.38.0.16   pi2.ax.saint-rossy.net
        >hello-world-664687dd5d-ctzn9   1/1       Running   0          3d        10.38.0.15   pi2.ax.saint-rossy.net
        >hello-world-664687dd5d-nszjk   1/1       Running   0          3d        10.38.0.14   pi2.ax.saint-rossy.net
        >hello-world-664687dd5d-px6bk   1/1       Running   0          3d        10.38.0.13   pi2.ax.saint-rossy.net
        >hello-world-664687dd5d-thwd2   1/1       Running   0          3d        10.38.0.12   pi2.ax.saint-rossy.net
    
9.  Use the external IP address (`LoadBalancer Ingress`) to access the Hello World application:
    
        curl http://<external-ip>:<port>
        >Hello, world!
        >Version: 1.0.0
        >Hostname: hello-world-664687dd5d-px6bk
    
    where  `<external-ip>`  is the external IP address (`LoadBalancer Ingress`) of your Service, and  `<port>`  is the value of  `Port`  in your Service description.

## Cleaning up

1. To delete the Service, enter this command:

        kubectl delete services my-service
        >service "my-service" deleted

2. To delete the Deployment, the ReplicaSet, and the Pods that are running the Hello World application, enter this command:

        kubectl delete deployment hello-world
        >deployment.extensions "hello-world" deleted

3. Verify everything has been deleted

        kubectl get deployments
        >No resources found.
        kube jsaint201$ kubectl get replicasets
        >No resources found.
        kube jsaint201$ kubectl get pods
        >No resources found.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjEwNzM3OTQ2NywtMTk3MzgzMDY3NCwtMT
M2ODg1MjMxNywxMjEzODkxOTcsMTM1MDE1Mzg2OCwtMTc5MDcw
NTI5MSwyMTYxNTM3NjAsOTI5NDY2MTksODk1NzI2ODQ0LC0xMT
AxNDYzMjUzLDE1MjgxNzMwNDQsMjAxNjE0ODkyNiw4ODU4NTY2
OTcsLTE1NjEwODgxMzFdfQ==
-->