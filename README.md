# openshift-host-prep
Small repo to include ansible files to prepare VM for OpenShift installation


- playbooks/base_packages.yaml<br>
Contains the base packages and other configurations required by the cluster or nodes

- playbooks/prepare_hosts.yaml<br>
Contains the main logic and instructions to prepare the nodes defined in inventory file

- playbooks/prepare_cluster.yaml<br>
Contains the instructions to prepare master server and required packages

- local_hosts_inventory.yaml
This is the file where you configure your local VMs, where the openshift packages should be donwloaded and installed.

- templates/openshift_inventory_file.template<br>
This is the inventory file that will be used as template for /etc/ansible/hosts in the cluster server. This file will be created once prepare_cluster.yaml is executed.



# How to run the scripts (from your local computer)
- Clone this repo to your local computer<br>
- Start up your VMs<br>
- Modify the file  "local_hosts_inventory.yaml" and replace with your server's name<br>
- Adjust file "templates/openshift_inventory_file.template" if you need to modify inventory file. The file provided was tested and is supposed to work.
- The following scripts must be executed:<br>
--- playbooks/prepare_hosts.yaml<br>
It will install and configure base packages<br>
--- playbooks/prepare_cluster.yaml<br>
Once base packages are installed, you may run this script to download and install cluster packages.<br>
File "/etc/ansible/hosts" will be created in the cluster server based on templates file (templates/openshift_inventory_file.template).


Once this is done. You can move forward deploying openshift by running prerequisites and deploy files, from inside your Cluster Server.

[root@okd-cluster ~]# ansible-playbook -i /etc/ansible/hosts /root/openshift-ansible-release-3.11/playbooks/prerequisites.yml
[root@okd-cluster ~]# ansible-playbook -i /etc/ansible/hosts /root/openshift-ansible-release-3.11/playbooks/deploy_cluster.yml