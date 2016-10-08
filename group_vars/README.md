### group_vars

manager.yml

````
---
anisble_connection: ssh
ansible_ssh_user: <username>
ansible_ssh_pass: <password>
````


window.yml

````
---
ansible_user: <username>
ansible_password: <password>
ansible_port: 5986
ansible_connection: winrm
ansible_winrm_server_cert_validation: ignore

````


worker.yml

````
---
anisble_connection: ssh
ansible_ssh_user: <username>
ansible_ssh_pass: <password>
````

