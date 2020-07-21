## install LAMP stack manually:
[LAMP stack installation](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04)
1. launch EC2 machine and Login into ec2 mchine
2. run below commands 
    ```
    sudo apt-get update 
    sudo apt-get install apache2 -y
    sudo systemctl restart apache2 or sudo service apache2 restart
    sudo apt-get install php libapache2-mod-php  php-mysql
    sudo systemctl restart apache2
    sudo nano /var/www/html/info.php  ## open this file
    ----
    <?php
    phpinfo();
    ?>
    ----
    ```
## linux convert into ansible task:
### TASKS:
 1. sudo apt-get update & sudo apt-get install apache2 convert into ansible task \
   * apt-get equivalent module in anisble (google search) 
    ```
    - name: update packges and install apache2
      apt: 
        name: apache2
        state: present
        update_cache: yes
    ```
 2. sudo systemctl restart apache2 convert into ansible task  \
  * service equivalent module in ansible
    ```
    - name: restart apache2
      service:
        name: apache2 
        state: started
    ```
  3. sudo apt-get install php libapache2-mod-php  php-mysql convert into ansible task \
    * install multiple packages in ansible 
     we have 3 ways to install multiple packages in ansible
     1. array
        ```
        - name: install multiple php packages using array
          apt:
            name: ["php","libapache2-mod-php","php-mysql"]
            state: present
        ```
     2. loops
        ```
        - name: install multiple php packages using loop
          apt:
           name: "{{ item }}"
           state: present
          loop:
           - php
           - libapache2-mod-php
           - php-mysql
        ```
     3. with_items
        ```
        - name: install multiple php packages using with_items
          apt:
           name: "{{ item }}"
           state: present
          with_items:
           - php
           - libapache2-mod-php
           - php-mysql
        ```
  4.  sudo systemctl restart apache2 convert into ansible task \
     * service equivalent module in ansible
       ```
       - name: restart apache2
         service:
           name: apache2 
           state: started
       ``` 
  5. copy file to remote nodes convert into ansible task \
     * copy file into remote nodes in ansible 
    ```
    - name: copy single line content into remote nodes
      copy: 
        content: '<?php phpinfo(); ?>'
        dest: /var/www/html/info.php 
    OR
    - name: copy file into remote nodes
      copy: 
        src: info.php
        dest: /var/www/html/info.php
    ```
    