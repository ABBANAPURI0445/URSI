## deployment
   1. eg war file presnet in jfrog artifactory
   2. deploy into tomcat8 application server 
## manual step:
   ```
   wget http://jfrog-gameoflife.war
   scp -i ansible.pem gameoflife.war ansible@10.0.0.5:/var/lib/tomcat8/webapps
   ``` 
## Playbook for deployment
   * deployment.yml
   ```
   - hosts: all
     become: yes
     tasks:
     - name: deploy application
       get_url:
        url: http://jfrog-gameoflife.war
        dest: /var/lib/tomcat8/webapps
        url_username: admin
        url_password: password
      notify: restart tomcat
     handlers:
     - name: restart tomcat
       service:
         name: tomcat8
         state: restarted
   ```
   *  vi inventory
      ```
      collection nodes ip address
      ```
   * these two files deployment.yml and inventory file store in remote repository
  
    