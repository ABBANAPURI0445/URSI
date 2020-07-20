## playbook: 
execute task on centos only
when: ansible_os_family == "RedHat"
execute task on ubuntu only
when: ansible_o_falimy == "Debian"
dont execute on debian family
when: ansible_os_family != "Debian"
execute this on specific host
when: ansible_hostname == "ip-172-31-35-10"
skip hostname 
when: ansible_hostname != "ip-172-31-35-10"


install httpd on centos: 
manual command: yum install httpd
yum install httpd convert into ansible module
```
 yum:
    name: httpd
    state: presnet
```
start httpd service:
manual commands: systemctl start httpd or service httpd start
service convert into ansible module ==> yum module
```
service:
    name: httpd
    state: started
```
* write a playbook for install httpd and start service on centos
  ```
  ---
  - hosts: all
    become: yes
    tasks:
    - name: install httpd on centos
      yum:
        name: httpd
        state: presnet
    - name: start httpd service
      service:
        name: httpd
        state: started
  ```
* write a playbook for create directory
   directory in ansible module  ==> file module
```
---
- hosts: all
  become: yes
  tasks:
  - name: create directory
    file: 
     path: /home/ansible/emptydir
     state: directory
```
* write playbook for create user jenkins
  manaul ==> adduser username
  convert into playbook 
  ```
  ---
  - hosts: all
    become: yes
    tasks:
    - name: create jenkins user
      user:
        name: jenkins
        state: present
 ```
### apply playbook to remote nodes
    ```
     -i or --inventory or --inventory-file 
     eg: 
     ansible-playbook -i myhost playbook.yml
     or
     ansible-playbook --inventory-file myhost playbook.yml
     or
     ansible-playbook --inventory myhost playbook.yml
    ```