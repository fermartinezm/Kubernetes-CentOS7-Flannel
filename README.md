# Kubernetes deployment on CentOS7, CNI: flannel
Kubernetes deployment on CentOS 7. It uses KVM to create the VMs (one master and two minions), Ansible as configuration manager to 
to perform automatic deployment and Openvswitch to bridge traffic between VMs and with the outside world.

## 1. Pre-requisites

- Localhost machine with CentOS 7
- Ansible

## 2. Prepare enviroment
First, you need check if the your localhost supports virtualization. You can do it typing the next command:
> egrep -c '(vmx|svm)' /proc/cpuinfo

If the result is 0 your localhost cannot support virtualization, otherwise it supports virtualization but you must be ensured it is enable in the BIOS.



Also, you need to install Ansible-2.7.9-1.e17. To install ansible yo need run the next commands with root user:

> yum install wget -y

> wget https://releases.ansible.com/ansible/rpm/release/epel-7-x86_64/ansible-2.7.9-1.el7.ans.noarch.rpm

> yum install ansible-2.7.9-1.el7.ans.noarch.rpm

or refer to https://docs.ansible.com/ansible/2.4/intro_installation.html
