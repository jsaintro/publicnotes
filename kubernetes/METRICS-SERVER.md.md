Look at this script for ideas
https://github.com/stefanprodan/k8s-scw-baremetal/blob/master/scripts/monitoring-install.sh

1. Deploy the arm metrics server 

kubectl apply -f https://raw.githubusercontent.com/stefanprodan/k8s-scw-baremetal/master/addons/metrics-server-arm.yaml

https://github.com/kubernetes-incubator/metrics-server/tree/master/deploy/1.8%2B

https://github.com/stefanprodan/k8s-scw-baremetal/blob/master/addons/metrics-server-arm.yaml

https://github.com/kubernetes-incubator/metrics-server/issues/73

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDI0MTI4MDYxLDU2MjcyMjM3NywxMzM4Mz
EwNzQsNzU0MDQ1NzYwXX0=
-->