This ansible role will create a K8s cluster on bare metal or VMs with Centos as the OS. You can have any number of nodes you like.

Each node in the cluster will act as a control plane and workers.

To run the role you will need to define your nodes like so

all:
  vars:
    ansible_connection: ssh
    ansible_ssh_user: root
  children:
    k8s:
      children:
        k8s_initial:
          hosts: 
            iomplprdkub01: 
        k8s_other:
          hosts: 
            iomplprdkub02:  
            iomplprdkub03:   

You must define one variable before running the role. haproxy_fqdn, and of course configure HAProxy to connecto to your cluster. You can install and configure HARorxy be using my ansible role