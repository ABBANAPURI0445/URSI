## Ansible Variable:
   * variables we can define in multiple places
     1. playbook
     2. command line   
     3. inventory file
     4. group vars
     5. hosts vars
     6. roles 
### define variable in playbook
    ```
    - hosts: all
      become: yes
      vars:
        package_name: htop
        web_package: nginx
      tasks:
      - name: install some package
        apt: 
          name: "{{ package_name }} "
          state: present
      - name: install webserver
        apt:
            name: "{{ web_package }}"
            state: present
    ```
### i want to install tree but i dont want to change value in Playbook pass variable in commandline 
    ```
    ansible-playbook -i inventory var.yml -e "package_name=htop" -e "web_package=apache2"
    ```
