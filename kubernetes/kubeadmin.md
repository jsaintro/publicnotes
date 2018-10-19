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

4. Access via a web browser

5. Create a user with permissions
kubectl create serviceaccount dashboard -n default
serviceaccount "dashboard" created
kubectl create clusterrolebinding dashboard-admin -n default \  
  --clusterrole=cluster-admin \  
  --serviceaccount=default:dashboard
  clusterrolebinding.rbac.authorization.k8s.io "dashboard-admin" created

1. Generate a signin token
kubectl get secret $(kubectl get serviceaccount dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode

create a bridge using kubectl proxy

   Note: you'll need to be vpned into one of the nodes or use kubectl proxy
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MTUwODQxMTEsLTIwNDk2NjMzNDUsLT
E3MDA5NjAwMjBdfQ==
-->