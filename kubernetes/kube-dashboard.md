1. apply the kube-dashboard yaml

        kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard-arm.yaml
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

1. create a bridge using kubectl proxy

Access the ui via the URL

http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/login

Enter the token from above

## Destroy the dashboard


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkzNjEwMzIzNCwxNjUxNDAyOTUzLDQzMD
A3NDA3Ml19
-->