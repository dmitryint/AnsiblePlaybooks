# Ansible Playbook to install and Configure Docker Engine and Swarm Cluster

Ansible playbook to install docker engine 1.2.1 and Swarm mode. This ansible playbook uses dynamic inventory to get the VM's info from Microsoft Azure using tags (Manager, Worker).

### Prerequisites
- Ansible 2.1.1
- Azure Python SDK https://github.com/Azure/azure-sdk-for-python
