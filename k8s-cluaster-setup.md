
# You can bootstrap a cluster as follows:

1. Initializes cluster master node:

 ```kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16```
2. Initialize cluster networking:
```
 kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml
```
3. (Optional) Create an nginx deployment:
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/website/master/content/en/examples/application/nginx-app.yaml
```
						  
```
kubeadm join 192.168.0.18:6443 --token 0giz3c.nl0p3n192hv62isw \
        --discovery-token-ca-cert-hash sha256:8d353999989e2ade5d3188390bdbf3c94ce1dbf57b29195cfa5fd221fdad8bdf 
```		
