### Init Kubernetes. **Only Master**
<br />
$ kubeadm config images pull
<br />
$ kubeadm init   --pod-network-cidr 10.244.0.0/16   --apiserver-advertise-address <IP_MASTER>

#After running the previous command we get an answer with this format:
<br />
#kubeadm join 10.6.20.32:6443 --token 33yjqi.nvrnz7kzn5ces3iy --discovery-token-ca-cert-hash sha256:7a5e210bf753d93084dfb2f0f63844ef23ea17885f62b95d774d1156b9154ae3
<br />
#We need to save it as it used in the next step to join the minions

### Start using the cluster. **Only Master**
<br />
$ mkdir -p $HOME/.kube
<br />
$ sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
<br />
$ sudo chown $(id -u):$(id -g) $HOME/.kube/config

