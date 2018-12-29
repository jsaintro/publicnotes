# NOTE Don't run this for a long amount of time on a standard rpi
The RPI controller will eventually get overloaded running this thing

Look at this script for ideas
https://github.com/stefanprodan/k8s-scw-baremetal/blob/master/scripts/monitoring-install.sh

Check the deployment at the end of this
https://linuxhint.com/kubernetes_metrics_server/

Note you'll have to change everything to arm Try just replacing `metrics-server-amd64` with `metric-server-arm`
1. Deploy all the rbac stuff and service stuff from
https://github.com/kubernetes-incubator/metrics-server/tree/master/deploy/1.8%2B
3. Deploy the arm metrics server 
kubectl apply -f https://raw.githubusercontent.com/stefanprodan/k8s-scw-baremetal/master/addons/metrics-server-arm.yaml
This is just the same yaml as the main deploy but with amd64->arm

https://github.com/kubernetes-incubator/metrics-server/tree/master/deploy/1.8%2B

https://github.com/stefanprodan/k8s-scw-baremetal/blob/master/addons/metrics-server-arm.yaml

https://github.com/kubernetes-incubator/metrics-server/issues/73

## Nuke it
https://raw.githubusercontent.com/kubernetes-incubator/metrics-server/master/deploy/1.8%2B/resource-reader.yaml

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY4ODg0MDQxNywtNDE0NjE2MjIwLDQ0NT
YxNTQ4Miw2OTU3MTE3OTAsLTQ3MDcxNjAwMiw0MjQxMjgwNjEs
NTYyNzIyMzc3LDEzMzgzMTA3NCw3NTQwNDU3NjBdfQ==
-->