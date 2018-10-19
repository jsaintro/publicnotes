1. apply the kube-dashboard yaml

        kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard-arm.yaml
        >secret/kubernetes-dashboard-certs created
        >serviceaccount/kubernetes-dashboard created
        >role.rbac.authorization.k8s.io/kubernetes-dashboard-minimal created
        >rolebinding.rbac.authorization.k8s.io/kubernetes-dashboard-minimal created
        >deployment.apps/kubernetes-dashboard created
        >service/kubernetes-dashboard created

2. Download the .kube/config from the master to your workstation

3. Find the ClusterIP/port

      kubectl get service 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk1MTE1NDY5MCwtMTcwMDk2MDAyMF19
-->