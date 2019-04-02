# Kubernetes-deployment
Kubernetes deployment on CentOS 7. It uses KVM to create the VMs (one master and two minions), Ansible as configuration manager to 
to perform automatic deployment and Openvswitch to bridge traffic between VMs and with the outside world.

# 1. Pre-requisites
Localhost machine with CentOS 7
Ansible

# 2. Prepare enviroment
You need check if the your localhost supports virtualization typing the next command:
> egrep -c '(vmx|svm)' /proc/cpuinfo
If the result is 0 your localhost cannot support virtualization otherwise it supports virtualization.
