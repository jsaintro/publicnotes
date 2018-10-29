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

> Written with [StackEdit](https://stackedit.io/).

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTk3NzE3NzI0LDY5NTcxMTc5MCwtNDcwNz
E2MDAyLDQyNDEyODA2MSw1NjI3MjIzNzcsMTMzODMxMDc0LDc1
NDA0NTc2MF19
-->