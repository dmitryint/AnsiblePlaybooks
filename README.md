# Ansible Playbook For Installation of Docker Swarm mode and MongoDB, ElasticSearch and Kibana cluster

Ansible playbook to install docker engine 1.12 and runs a swarm cluster of MongoDB, Elasticsearch, and Kibana. This ansible playbook uses dynamic inventory to get the VM's info from Microsoft Azure using tags (Manager, Worker). 

### Prerequisites
- Ansible 2.1.1
- Azure Python SDK https://github.com/Azure/azure-sdk-for-python

### Setup
##### Get playbooks 

To get the latest update playbooks from the git repo

``` 
cd /etc/ansible/AnsiblePlaybooks/
ansible-playbook playbook.yml --ask-vault-pass 
```

Change the /roles/get-playbook/vars/main file in the playbook with your details. To edit the file with vault use 

```ansible-vault edit foo.yml```

For more ansible vault commands refer http://docs.ansible.com/ansible/playbooks_vault.html

Credentials are encrypted in ansible playbook using the Ansible vault. You need to provide the vault password to run the playbook.

##### Docker Engine 1.12
To install the docker-engine on ubuntu 16.04 manager and worker nodes 

```sudo ansible-playbook -i azure_rm.py engine.yml```

azure_rm.py file would fetch the dynamic inventory list from Azure according to the tags given 

##### Docker Swarm 
To install and configure docker in Swarm mode 

```ansible-playbook -i azure_rm.py swarm.yml```

To check the docker swarm cluster status ssh into the manager and worker nodes and use the below command 

```docker info```

To check manager status use the below command on manager

``` docker node ls ```

##### MongoDB Elasticsearch Kibana stack 

To build up the docker images and run the stack in swarm mode 

```ansible-playbook -i azure_rm.py elastic_swarm.yml --ask-vault-pass```

###### To check cluster status
To check all the services running in the swarm cluster 

```docker service ps``` 

It will show all the running container along with the replication factor of each container 

To check status of a specific service 

``` docker service ps kibana ```

 It shows the running status on which worker or manager node the container is running
 
 To inspect a service
 
 ``` docker service inspect kibana```
 
##### Ports:

Docker swarm will Map the Navigator Elastic Search Cluster to the following Ports

| Container              |  Address/Port     |
| -----------------------| :-----------------|
| Mongo primary node     | `Vm_public_ip:27017` |
| Mongo secondary node   | `Vm_public_ip:27018` |
| Mongo secondary node   | `Vm_public_ip:27019` |
| Elasticsearch node     | `Vm_public_ip:9200`  |
| Kibana node            | `Vm_public_ip:5601`  |
 
###### Verify Elastic Search Indexes 

`http://Vm_public:9200/_cat/indices?v `

It would show all the indexes present in elastisearch

TO Verify logs in Kibana 

`http://Vm_public:5601 `


