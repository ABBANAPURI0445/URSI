## tags
   [tags reference](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tags.html)
   ```
   tags.yml
   ---
  - hosts: all 
    become: yes
    tasks:
    - name: install tomcat8 in ubuntu 
      apt: 
        name: tomcat8 
        state: present 
        update_cache: yes 
      tags: 
      - ubuntu-appserver 
    - name: install tomcat8 in centos 
      yum: 
        name: tomcat 
        state: present 
      tags: 
      - centos-appserver
    - name: create directory
      file:
       path: /home/ansible/dummy
       state: directory
      tags:
      - directory
    ``` 
    * ansible-playbook -i inv tags.yml --skip-tags "centos-appserver"
    * ansible-playbook -i inv tags.yml --tags "ubuntu-appserver,directory"