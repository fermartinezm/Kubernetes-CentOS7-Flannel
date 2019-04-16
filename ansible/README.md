# Installation using Ansible
In this section there are all the necessary files for an automated installation of Kubernetes v.1.14 in CentOS7.

## 1. Pre-requisites
- You need have Ansible installed in the computer where the installation is launched. You can install it using the command `yum install ansible` or you can find more information [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html?extIdCarryOver=true&sc_cid=701f2000001OH7YAAW#latest-release-via-dnf-or-yum). The last ansible version checked is 2.7.9.

- You need at least two machines or virtual machines, one master and one minion. By default the project uses one master and two minions.

- Configure the file `hosts` with the machines IPs and hostnames.

## 2. Installation options
### - Add more minions
To add more minions you only need to modify the file `hosts`, adding the new minion IP and hostname.

Example:
<br />
[master]
<br />
k8s-master1     ansible_host=192.168.1.201

[minions]
<br />
k8s-minion2     ansible_host=192.168.1.202
<br />
k8s-minion3     ansible_host=192.168.1.203
<br />
**k8s-minion4     ansible_host=192.168.1.204**

[cluster:children]
<br />
master
<br />
minions

### - Install other CNI
If you want use a different CNI you only need comment the last four lines of the `site.yml` file and use another CNI. You can find more information about CNIs [here](https://kubernetes.io/docs/concepts/cluster-administration/networking/).

Example:
<br />
#- hosts: master
<br />
#become: true
<br />
#roles:
<br />
#- flannel

## 3. Installation
You only need run the command `ansible-playbook -i hosts site.yml` inside the ansible directory.
