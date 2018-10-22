# Metal LB

## Install
1. Download the yaml and adapt for rpi

        wget https://raw.githubusercontent.com/google/metallb/v0.7.3/manifests/metallb.yaml

2. Edit the yaml to use the arm64 version of all images

        vi metallb.yaml
        ...
        image: metallb/speaker:v0.7.3-arm
        ...
        image: metallb/controller:v0.7.3-arm
        ...

     Note: All rPi Os'es are 32 bit even though the Rpi3 can support 64bit
3. Apply the manifest

        kubectl apply -f metallb.yaml
        >namespace/metallb-system created
        >serviceaccount/controller created
        >serviceaccount/speaker created
        >clusterrole.rbac.authorization.k8s.io/metallb-system:controller created
        >clusterrole.rbac.authorization.k8s.io/metallb-system:speaker created
        >role.rbac.authorization.k8s.io/config-watcher created
        >clusterrolebinding.rbac.authorization.k8s.io/metallb-system:controller created
        >clusterrolebinding.rbac.authorization.k8s.io/metallb-system:speaker created
        >rolebinding.rbac.authorization.k8s.io/config-watcher created
        >daemonset.apps/speaker created
        >deployment.apps/controller created

4. Wait for the pods to come up

        kubectl get pods -n metallb-system
        >NAME                          READY   STATUS    RESTARTS   AGE
        >controller-6f85c5444d-k58q4   1/1     Running   0          2m24s
        >speaker-2b75v                 1/1     Running   0          2m24s
        >speaker-dqztl                 1/1     Running   0          2m24s

5. Configure the loadbalancer
    1. Download the template

             wget https://raw.githubusercontent.com/google/metallb/v0.7.3/manifests/example-layer2-config.yaml

    2. Edit the template and add your IP range

            vi example-layer2-config.yaml
            >addresses:
            >  - 192.168.86.101-192.168.86.200

         Note: The IP range is IP's that the loadbalancer will create on the public network.  Obviously you need to make sure there are no conflicts with DHCP etc...
         Note: We use layer2 as we're not using a BGP compatible switch.  

    3. Apply the configuration

            kubectl apply -f example-layer2-config.yaml
            >configmap/config created

## Test the loadbalancer



                  
