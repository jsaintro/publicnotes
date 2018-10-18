
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
        >deaemonset.extensions/traefik-ingress-controller created
        >service/traefik-ingress-service created

4. Monitor the ds creation

        kubectl get ds traefik-ingress-controller --namespace=kube-system
        >NAME                         DESIRED   CURRENT   READY     UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
        >traefik-ingress-controller   2         2         0         2            0           <none>          2m
        kubectl get pods --namespace=kube-system -o wide | egrep "NAME|traefik"
        >NAME                                             READY     STATUS              RESTARTS   AGE       IP              NODE
        >traefik-ingress-controller-7lp49                 0/1       ContainerCreating   0          5m        <none>          pi2.ax.saint-rossy.net
        >traefik-ingress-controller-z846x                 0/1       ContainerCreating   0          5m        <none>          pi3.ax.saint-rossy.net
    This will take about 5 minutes cause ... raspberry pi

5. Check the logs of one of the pods to make sure it's running properly

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

## Appendix: Daemonset Notes
In order to get the deamon set to work correctly you need to do this guys workarounds
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk3MzczNDMxLDEwNDE3Mjc5NzQsNDkyNz
A5ODg0LC0yMDMxOTUyMTg4LC0yMDAxMDMwNjAxLDExNTc4MTIx
NzcsLTg0NTgyNDAxNiwtMTc4NTM1OTQ2OCwxNzQ2NjIxNDA5LC
02NjE2NTE1NzQsNTM2MTEyMjkzLDExNTg1NTc2NTMsLTEwODE5
MzIzNjYsLTk1NDMwMTQ5MywtMTI1Mjg3NDcwNSwtMTg4MjcwNT
Y0NV19
-->