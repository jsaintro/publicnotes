Look at this script for ideas
https://github.com/stefanprodan/k8s-scw-baremetal/blob/master/scripts/monitoring-install.sh

Check the deployment at the end of this
https://linuxhint.com/kubernetes_metrics_server/

Note you'll have to change everything to arm Try just replacing `metrics-server-amd64` with `metric-server-arm`
1. Deploy the arm metrics server 

kubectl apply -f https://raw.githubusercontent.com/stefanprodan/k8s-scw-baremetal/master/addons/metrics-server-arm.yaml

https://github.com/kubernetes-incubator/metrics-server/tree/master/deploy/1.8%2B

https://github.com/stefanprodan/k8s-scw-baremetal/blob/master/addons/metrics-server-arm.yaml

https://github.com/kubernetes-incubator/metrics-server/issues/73

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ3MDcxNjAwMiw0MjQxMjgwNjEsNTYyNz
IyMzc3LDEzMzgzMTA3NCw3NTQwNDU3NjBdfQ==
-->