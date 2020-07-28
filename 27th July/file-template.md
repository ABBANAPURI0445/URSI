## file
   1. file contains static content
   2. it will never change
   3. create file file.txt
      ```
      hi i {{ username }}
      my operating system is {{ ansible_os_family }}/ubuntu18.04
      ```
   4. copy static content into ansible nodes from ansible control server
      1. static.yml
         ```
         - hosts: all 
           become: yes
           vars:
            username: ansible
           tasks: 
           - name: copy static content into ansible nodes
             copy: 
                src: /home/ansible/file.txt
                dest: /home/ansible/static-content 
         ```
      2. run playbook
         ```
         ansible-playbook -i inv static.yml
      3. login into node execute below command
         ```
          /home/ansible/static-content 
         ``` 
         * o/p display like below
           ```
           hi i {{ username }}
           my operating system is {{ ansible_os_family }}/ubuntu18.04
           ``` 

## template 
   * template conatins dynamic content
   * it change with variable and facts
   1. create file dynamic.j2
      ```
      hi i {{ username }}
      my operating system is {{ ansible_os_family }}/ubuntu18.04
      ```
   2. copy static content into ansible nodes from ansible control server
      1. dynamic.yml
         ```
         - hosts: all 
           become: yes
           vars:
            username: ansible
           tasks: 
           - name: copy static content into ansible nodes
             template: 
                src: /home/ansible/dynamic.j2
                dest: /home/ansible/dynamic-content 
         ```
      2. run playbook
         ```
         ansible-playbook -i inv dynamic.yml
      3. login into node execute below command
         ```
          /home/ansible/dynamic-content 
         ``` 
         * o/p display like below
           ```
           hi i ansible
           my operating system is Debian/ubuntu18.04
           ``` 