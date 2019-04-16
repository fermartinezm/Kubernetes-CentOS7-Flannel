### Install Kubernetes. **Master and Minions**
<br />
$ cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
        https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
exclude=kube*
EOF
<br />
$ yum install --assumeyes --disableexcludes kubernetes kubeadm-1.14.0 kubectl-1.14.0 kubelet-1.14.0

### Restart and enable kubelet service. **Master and Minions**
$ systemctl daemon-reload | systemctl start kubelet | systemctl enable kubelet

