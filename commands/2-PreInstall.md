### Set hostnames
#Set hostnames. **Master and Minions**
<br />
$ hostnamectl set-hostname <HOSTNAME_MASTER>
<br />
$ hostnamectl set-hostname <HOSTNAME_MINION1>
<br />
$ hostnamectl set-hostname <HOSTNAME_MINION2>
<br />
$ ...

### Modify /etc/hosts file adding. **Master and Minions**
<br />
$ vi /etc/hosts
<br />
<IP_MASTER> <HOSTNAME_Master>
<br />
<IP_MINION1> <HOSTNAME_MINION1>
<br />
<IP_MINION2> <HOSTNAME_MINION2>
<br />
...

### Disbale Selinux. **Master and Minions**
<br />
$ setenforce 0
<br />
$ sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/selinux/config

### Activate br_netfilter. **Master and Minions**
<br />
$ modprobe br_netfilter
<br />
$ cat <<EOF >  /etc/sysctl.d/k8s.conf
<br />
net.bridge.bridge-nf-call-ip6tables = 1
<br />
net.bridge.bridge-nf-call-iptables = 1
<br />
EOF
<br />
$ sysctl --system

### Open firwwalld ports. **Master and Minions**
<br />
$ firewall-cmd --add-masquerade --permanent
<br />
$ firewall-cmd --add-port=10250/tcp --permanent
<br />
$ firewall-cmd --add-port=8472/udp --permanent
<br />
$ firewall-cmd --add-port=6443/tcp --permanent
<br />
$ systemctl restart firewalld

### Disable swap memory. **Master and Minions**
<br />
$ swapoff -a
<br />
$ vi /etc/fstab
<br />
# Comment the line that looks like: #/dev/mapper/centos-swap swap                    swap    defaults        0 0


