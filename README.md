## Ansibl playbook to install Apache Webserver 

Ansible playbook to install Apache webserver. This ansible playbook uses dynamic inventory to get the VM's info from Microsoft Azure using tags (webserver, apache). 

### Prerequisites
- Ansible 2.1.1
- Azure Python SDK https://github.com/Azure/azure-sdk-for-python

### Setup
Create a VM for apache from the ansible slave template.For process of running template deploymnet refer to the document
**Make sure to give the tag webserver:apache while creating the VM from ansible slave image**
##### Get playbooks 

To get the latest update playbooks from the git repo

``` 
cd /etc/ansible/AnsiblePlaybooks/
ansible-playbook playbook.yml --ask-vault-pass 
```
Edit the /etc/ansible/AnsiblePlaybooks/group_vars/all file with ansible vault and enter the username and password of the the vm on which you want to install ansible. 

```ansible-vault edit group_vars/all```

Change the roles/get-playbook/vars/main file in the playbook with your add user password and subscription. This will be used to connect to azure api. For creating the ad_user, password and subscriptionid refer the documnet It includes all the details with visuals. To edit the file with vault use 

```ansible-vault edit roles/get-playbook/vars/main ```

Credientials are encyrpted in ansible playbook using the Ansible vault. You need to provide the vault password to run the playbook.

##### Run Apache installation playbook 
To install the apache on ubuntu 16.04 

```sudo ansible-playbook -i azure_rm.py apache.yml --ask-vault-pass```

azure_rm.py file would fetch the dyanamic inevntory list from Azure according to the tags given 

#### Verifying the Apache installation

To verify the installation of apache open the public ip of the vm in the browser 

```http://ip_of_vm ```