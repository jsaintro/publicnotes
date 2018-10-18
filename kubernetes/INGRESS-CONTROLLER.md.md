
# Ingress Controller Setup

This is requred for standalone K8s installations to allow Ingress loadbalancing.

## Based on 
https://www.infralovers.com/en/articles/2017/04/22/kubernetes-and-traefik-on-raspberry/
https://blog.hypriot.com/post/setup-kubernetes-raspberry-pi-cluster/
https://docs.traefik.io/user-guide/kubernetes/
https://medium.com/@evnsio/managing-my-home-with-kubernetes-traefik-and-raspberry-pis-d0330effea9a

## Setup RBAC

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

1.  Use the Treefik 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg0MjUwNzkyLC0xMDgxOTMyMzY2LC05NT
QzMDE0OTMsLTEyNTI4NzQ3MDUsLTE4ODI3MDU2NDVdfQ==
-->