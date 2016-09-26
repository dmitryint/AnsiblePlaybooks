## Ansible Playbooks 

### Prerequisites
- Ansible 2.1.1
- Azure Python SDK https://github.com/Azure/azure-sdk-for-python

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

