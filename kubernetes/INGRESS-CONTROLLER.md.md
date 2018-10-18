
# Ingress Controller Setup

This is required for standalone K8s installations to allow Ingress loadbalancing.

## Based on 
https://www.infralovers.com/en/articles/2017/04/22/kubernetes-and-traefik-on-raspberry/
https://blog.hypriot.com/post/setup-kubernetes-raspberry-pi-cluster/
https://docs.traefik.io/user-guide/kubernetes/
https://medium.com/@evnsio/managing-my-home-with-kubernetes-traefik-and-raspberry-pis-d0330effea9a

## Setup RBAC Permissions for Traefik

### Verify RBAC is enabled
1. Determine if you're configured for RBAC
    1. Get the api server hostname

            kubectl get pods --namespace=kube-system | grep api | awk {'print $1'}
            >kube-apiserver-pi1.ax.saint-rossy.net

     2. Check if the api server was started with the RBAC switch

            kubectl describe pod kube-apiserver-pi1.ax.saint-rossy.net --namespace=kube-system | grep authorization-mode
            >--authorization-mode=Node,RBAC

        If you see `RBAC` the RBAC is enabled

### Bind Traefik to the ClusterRole

1.  Apply the Traefik provided yaml to our Kubernetes cluster

        kubectl apply -f https://raw.githubusercontent.com/containous/traefik/master/examples/k8s/traefik-rbac.yaml
        clusterrole.rbac.authorization.k8s.io/traefik-ingress-controller created
        clusterrolebinding.rbac.authorization.k8s.io/traefik-ingress-controller created

2. Verify the binding

        kubectl describe clusterrolebinding.rbac traefik-ingress-controller
        >Name:         traefik-ingress-controller
        >Labels:       <none>
        >Annotations:  kubectl.kubernetes.io/last-applied-configuration={"apiVersion":"rbac.authorization.k8s.io/v1beta1","kind":"ClusterRoleBinding","metadata":{"annotations":{},"name":"traefik-ingress-controller","namespa...
        >Role:
        >  Kind:  ClusterRole
        >  Name:  traefik-ingress-controller
        >Subjects:
        >  Kind            Name                        Namespace
        >  ----            ----                        ---------
        >  ServiceAccount  traefik-ingress-controller  kube-system

## Install the Deployment
Chose to go with deployment vs daemon set as it's lighter weight and requires less hacking to get it working
1. Apply the deployment yaml

        kubectl apply -f https://raw.githubusercontent.com/containous/traefik/master/examples/k8s/traefik-deployment.yaml
        >serviceaccount/traefik-ingress-controller created
        >deployment.extensions/traefik-ingress-controller created
        >service/traefik-ingress-service created

2. Monitor the deployment creation

        kubectl get deployment traefik-ingress-controller --namespace=kube-system
        >NAME                         DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
        >traefik-ingress-controller   1         1         1            1           1h
        kubectl get pods --namespace=kube-system -o wide | egrep "NAME|traefik"
        >NAME                                             READY     STATUS    RESTARTS   AGE       IP              NODE
        >traefik-ingress-controller-6f6d87769d-22tm9      1/1       Running   0          1h        10.32.0.5       pi3.ax.saint-rossy.net

    This will take about 5 minutes cause ... raspberry pi

3. Check the logs of one of the pods to make sure it's running properly

        kubectl logs traefik-ingress-controller-7lp49 --namespace=kube-system
        >time="2018-10-18T04:37:02Z" level=info msg="Traefik version v1.7.3 built on 2018-10-15_10:13:00AM"
        >time="2018-10-18T04:37:02Z" level=info msg="\nStats collection is disabled.\nHelp us improve Traefik by turning this feature on :)\nMore details on: https://docs.traefik.io/basics/#collected-data\n"
        >time="2018-10-18T04:37:02Z" level=info msg="Preparing server traefik &{Address::8080 TLS:<nil> Redirect:<nil> Auth:<nil> WhitelistSourceRange:[] WhiteList:<nil> Compress:false ProxyProtocol:<nil> ForwardedHeaders:0x496e040} with readTimeout=0s writeTimeout=0s idleTimeout=3m0s"
        >time="2018-10-18T04:37:02Z" level=info msg="Preparing server http &{Address::80 TLS:<nil> Redirect:<nil> Auth:<nil> WhitelistSourceRange:[] WhiteList:<nil> Compress:false ProxyProtocol:<nil> ForwardedHeaders:0x496e030} with readTimeout=0s writeTimeout=0s idleTimeout=3m0s"
        >time="2018-10-18T04:37:02Z" level=info msg="Starting server on :8080"
        >time="2018-10-18T04:37:02Z" level=info msg="Starting server on :80"
        >time="2018-10-18T04:37:02Z" level=info msg="Starting provider configuration.ProviderAggregator {}"
        >time="2018-10-18T04:37:02Z" level=info msg="Starting provider *kubernetes.Provider {\"Watch\":true,\"Filename\":\"\",\"Constraints\":[],\"Trace\":false,\"TemplateVersion\":0,\"DebugLogGeneratedTemplate\":false,\"Endpoint\":\"\",\"Token\":\"\",\"CertAuthFilePath\":\"\",\"DisablePassHostHeaders\":false,\"EnablePassTLSCert\":false,\"Namespaces\":null,\"LabelSelector\":\"\",\"IngressClass\":\"\",\"IngressEndpoint\":null}"
        >time="2018-10-18T04:37:02Z" level=info msg="ingress label selector is: \"\""
        >time="2018-10-18T04:37:02Z" level=info msg="Creating in-cluster Provider client"
        >time="2018-10-18T04:37:04Z" level=info msg="Server configuration reloaded on :8080"
        >time="2018-10-18T04:37:04Z" level=info msg="Server configuration reloaded on :80"

4. Get the dynamically assigned NodePorts

        kubectl get service traefik-ingress-service --namespace=kube-system
        >NAME                      TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)                       AGE
        >traefik-ingress-service   NodePort   10.102.147.142   <none>        80:32285/TCP,8080:30600/TCP   2h

    Here we see 80 has been assigned 32285 and 8080 (admin port) has been assigned 30600.  These ports are available on each node in the cluster.

5. Configure your external gateway to map port 80 -> port 32285 on any of the nodes in the cluster.

## Simple example 
## Appendix: Daemonset Notes
In order to get the deamon set to work correctly you need to do this guys workarounds
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExODYxNjU2NjgsMTA0MTcyNzk3NCw0OT
I3MDk4ODQsLTIwMzE5NTIxODgsLTIwMDEwMzA2MDEsMTE1Nzgx
MjE3NywtODQ1ODI0MDE2LC0xNzg1MzU5NDY4LDE3NDY2MjE0MD
ksLTY2MTY1MTU3NCw1MzYxMTIyOTMsMTE1ODU1NzY1MywtMTA4
MTkzMjM2NiwtOTU0MzAxNDkzLC0xMjUyODc0NzA1LC0xODgyNz
A1NjQ1XX0=
-->