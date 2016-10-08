
## Docker Engine 

Version: Lattest

````
 cd /etc/ansible/AnsiblePlaybooks/
 sudo ansible-playbook azure_rm.py engine.yml --ask-vault-pass
````

vars/main  
````
---
storage_account: <storage_account>
storage_account_key: <storage_account_key>
````
