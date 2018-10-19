## Steps for All Nodes
1.  Install Latest release of Docker

```
jsaintrocc@pi3:~$ curl -sSL get.docker.com | sh && \
sudo usermod jsaintrocc -aG docker
```

1. Logout and log back in again
    This is to apply the docker group registration
    
3.  Validate version of docker

```
jsaintrocc@pi3:~$ docker version | egrep "Client|Server|Version"
Client:
 Version:      18.05.0-ce
Server:
  Version:      18.05.0-ce
```

The current Kubernetes blessed version of Docker is 17.03. For my raspberry pi, I installed Docker 18.05.0-ce, haven’t seen any problem yet.

3. Turn off swap

```
jsaintrocc@pi3:~$  sudo dphys-swapfile swapoff && \
sudo dphys-swapfile uninstall && \
sudo update-rc.d dphys-swapfile remove
```

To validate:

```
jsaintrocc@pi3:~$  sudo swapon --summary
```

Should print out nothing.

3. Add cpu, memory into cgroup recouces

And this line to the very end and don't add a cairrage return at the end
```
sudo vi /boot/cmdline.txt
cgroup_enable=cpuset cgroup_enable=memory
```
4. REBOOT

```
sudo reboot
```

6. Validate cgroups are enabled

```
jsaintrocc@pi2:~ $ cat /proc/cgroups | egrep "cpuset|memory"
cpuset	8	1	1
memory	2	70	1
```

1's in the 3rd column indicate both are enabled

6. Install Kubernetes

```
jsaintrocc@pi2:~ $ curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add - && \
echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list && \
sudo apt-get update -q && \
sudo apt-get install -qy kubeadm
```
Note kubernetes-xenial should work for raspbian which is currently base on stretch.  Technically you should be able to use kubernetes-yakkety but it's missing raspberry pi cpu support.  Also the debian versions don't contain all the packages.

7. Verify

```
jsaintrocc@pi2:~ $ kubeadm version
kubeadm version: &version.Info{Major:"1", Minor:"11", GitVersion:"v1.11.0", GitCommit:"91e7b4fd31fcd3d5f436da26c980becec37ceefe", GitTreeState:"clean", BuildDate:"2018-06-27T20:14:41Z", GoVersion:"go1.10.2", Compiler:"gc", Platform:"linux/arm"}
```

9. Till this point, all steps above should be done in all Raspberry nodes. Next step is needed  **ONLY**  for master node:

## Additional Steps for Master Node Only 

1. Find the your default interface
  1. Get the default route
```
jsaintrocc@pi2:~ $ route | grep default
default         testwifi.here   0.0.0.0         UG    303    0        0 wlan0
```

So the default interface is wlan0

  1. Get the ip of the default interface
```
jsaintrocc@pi2:~ $ ip -4 addr show dev wlan0
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    inet 192.168.86.11/24 brd 192.168.86.255 scope global wlan0
       valid_lft forever preferred_lft forever
```
Note: Obviously the IP shouldn't change (Either static or reserved in DHCP etc...)

1. Prepull kubernetes images
```
kubeadm config images pull
```
Note: It's not strictly required you do this before hand but it validates you're pulling the images correctly etc..

Then I initialized this main node

```
sudo kubeadm init --apiserver-advertise-address=192.168.86.11
```

This command takes around 2–5 minutes to run and in the end, it is gonna spit out a command telling you how to join the Kubernetes cluster from worker nodes, something like:

7. Save that command and run the snippet given to you on the command-line in master node:

```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

8.  Install the CNI network plugin (Required to get things working)
  1. sysctl net.bridge.bridge-nf-call-iptables=1
  2. Run the weave network cni plugin pod
   
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
```
Note if kube-controller-manager is in CrashLoopBackOff may need to restart and reapply the above.  Note 
What for cluster to come up with `kubectl get pods --all-namespaces` takes a while like 5 min

https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/#pod-network
9.  Lets see whats running
  
```
jsaintrocc@pi1:~ $ kubectl get pods --namespace kube-system
NAME                                             READY     STATUS             RESTARTS   AGE
coredns-78fcdf6894-h9n7c                         0/1       Pending            0          12m
coredns-78fcdf6894-rgngd                         0/1       Pending            0          12m
etcd-pi1.ax.saint-rossy.net                      1/1       Running            0          11m
kube-apiserver-pi1.ax.saint-rossy.net            1/1       Running            0          11m
kube-controller-manager-pi1.ax.saint-rossy.net   0/1       CrashLoopBackOff   6          12m
kube-proxy-pncpz                                 1/1       Running            0          12m
kube-scheduler-pi1.ax.saint-rossy.net            1/1       Running            0          11m
```

11. Join the workers nodes (On each worker node)
sudo kubeadm join 192.168.86.11:6443 --token XXXXXX --discovery-token-ca-cert-hash sha256:YYYYY


	[WARNING RequiredIPVSKernelModulesAvailable]: the IPVS proxier will not be used, because the following required kernel modules are not loaded: [ip_vs_sh ip_vs ip_vs_rr ip_vs_wrr] or no builtin kernel ipvs support: map[ip_vs:{} ip_vs_rr:{} ip_vs_wrr:{} ip_vs_sh:{} nf_conntrack_ipv4:{}]
you can solve this problem with following methods:
 1. Run 'modprobe -- ' to load missing kernel modules;
12. Provide the missing builtin kernel ipvs support


13. Run the  `sudo kubeadm join xx`  command in workers. Validate:

        $root@raspberrypi-7:~# kubectl get nodes  
        NAME             STATUS    ROLES     AGE       VERSION  
raspberrypi-13   Ready     <none>    22h       v1.10.5  
raspberrypi-7    Ready     master    23h       v1.10.5  
raspberrypi-8    Ready     <none>    23h       v1.9.1
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkxMTk3NjU3OSwtNzMxNzk2NTJdfQ==
-->