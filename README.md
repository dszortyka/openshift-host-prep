# openshift-host-prep
Small repo to include ansible files to prepare VM for OpenShift installation


- playbooks/base_packages.yaml<br>
Contains the base packages and other configurations required by the cluster or nodes

- playbooks/prepare_hosts.yaml
Contains the main logic and instructions to prepare the nodes defined in inventory file

- playbooks/prepare_cluster.yaml
Contains the instructions to prepare master server and required packages

- hosts.yaml
Inventory file where the hosts and main variables are defined