## Ansible Control server:
  1. install ansible software 
     1. launch EC2 machine (t2.micro) 
     2. login into EC2 machine
     3. run below commands
     ```
      sudo apt update
      sudo apt install software-properties-common
      sudo apt-add-repository --yes --update ppa:ansible/ansible
      sudo apt install ansible
     ```
 2. create user 
    ```
     addsuer ansible
    ```
 3. assign sudo permission
    ```
     visudo
     or
     vi /etc/sudoers
    ```
 4. enable passwd authentication
    ```
     vi /etc/ssh/sshd_config
    ```
 5. restart sshd
    ```
     systemctl restart sshd
    ```
 6. generate ssh keys from ansible user
    ```
     su ansible 
     ssh-keygen
    ```


## setup Nodes:
  1. create user
  2. assign sudo permission
  3. enable passwd authentication
  4. restart sshd

## Master slave connection:
  1. login into ACS 
     ```
     ssh ansible@ACSIpaddres
     ```
  2. share ssh keys (id_rsa.pb) to nodes 
     ```
     ssh-copy-id nodeusername@nodeipaddress
     ```
