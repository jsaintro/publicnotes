
# Ingress Controller Setup

This is requred for standalone K8s installations to allow Ingress loadbalancing.

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

## Install the Daemonset

Note: You can do a regular deployment or a daemonset.  By default the suggest daemonset

1. Download the daemonset template (We need to modify it to work with the arm architecture
 wget
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDg3MjMyNzYzLDUzNjExMjI5MywxMTU4NT
U3NjUzLC0xMDgxOTMyMzY2LC05NTQzMDE0OTMsLTEyNTI4NzQ3
MDUsLTE4ODI3MDU2NDVdfQ==
-->