### Install Docker. **Master and Minions**
<br />
$ yum install -y yum-utils device-mapper-persistent-data lvm2
<br />
$ yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
<br />
$ yum install -y docker-ce-18.09.4

### Change Docker group to systemd. **Master and Minions**
<br />
$ mkdir /etc/docker
<br />
$ cat > /etc/docker/daemon.json <<EOF
<br />
{
<br />
  "exec-opts": ["native.cgroupdriver=systemd"],
<br />
  "log-driver": "json-file",
<br />
  "log-opts": {
<br />
    "max-size": "100m"
<br />
  },
<br />
  "storage-driver": "overlay2",
<br />
  "storage-opts": [
<br />
    "overlay2.override_kernel_check=true"
<br />
  ]
<br />
}
<br />
EOF
<br />
$ mkdir -p /etc/systemd/system/docker.service.d

### Start and enable Docker service. **Master and Minions*
<br />
$ systemctl daemon-reload | systemctl start docker | systemctl enable docker
