
# Ingress Controller Setup

This is requred for standalone K8s installations to allow Ingress loadbalancing.

## Based on 
https://www.infralovers.com/en/articles/2017/04/22/kubernetes-and-traefik-on-raspberry/
https://blog.hypriot.com/post/setup-kubernetes-raspberry-pi-cluster/
https://docs.traefik.io/user-guide/kubernetes/
https://medium.com/@evnsio/managing-my-home-with-kubernetes-traefik-and-raspberry-pis-d0330effea9a

## Setup RBAC

1. Determine if you're configured for RBAC
	1. Get the api server hostname

            kubectl get pods --namespace=kube-system | grep api | awk {'print $1'}
kube-apiserver-pi1.ax.saint-rossy.net
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgwMzAwOTQzNywtMTI1Mjg3NDcwNSwtMT
g4MjcwNTY0NV19
-->