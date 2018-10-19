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

        kubectl get services kubernetes-dashboard --namespace=kube-system
        >NAME                   TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)   AGE
        >kubernetes-dashboard   ClusterIP   10.104.195.122   <none>        443/TCP   9m
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI0OTAyODg2MCwtMTcwMDk2MDAyMF19
-->