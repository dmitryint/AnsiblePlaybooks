## Ansible Playbook to Install Apache Webserver 

##### Run Apache installation playbook 
To install the apache on ubuntu 16.04 

```sudo ansible-playbook -i azure_rm.py apache.yml --ask-vault-pass```

azure_rm.py file would fetch the dyanamic inevntory list from Azure according to the tags given 

#### Verifying the Apache installation

To verify the installation of apache open the public ip of the vm in the browser 

```http://ip_of_vm ```
