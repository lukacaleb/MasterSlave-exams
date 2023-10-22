# EXAM PROJECT DOCUMENTATION 
### 1. the project contains the automation and provisioning of two Ubuntu-based servers, named “Master” and “Slave”, using Vagrant, with a bash script to automate the deployment of a LAMP (Linux, Apache, MySQL, PHP) stack, and cloned a PHP application from GitHub, with all necessary packages, and configured Apache web server and MySQL while using ansible to execute the bash script on the Slave node and cronjob to create check the server's uptime every 12:00am. the bash script is reusable and readable and can be accessible through the following repository: https://github.lukacaleb.master-slave/master-slave.git

### 2. Provisioning of "master" and "slave"
the file "vagrant-master.sh" when runned/executed, spines up the two ubuntu master and slave machines while creating a vagrantfile.


### 3. laravel deployment on master node
the file "lamp-master.sh" deploys laravel cloned from github repository only on the master node. https://github.com/laravel/laravel.

![laravel on master node](<snapshorts/successfuly install laravel and all dependencies.PNG>)


![laravel on master node](<snapshorts/laravel successfuly installed.PNG>)

![master IP@192.168.30.20](<snapshorts/laravel page with master ip adress.PNG>)


### 4. the ansible playbook
in the absible-playbook directory contains ansible.cfg, inventory, play-slave.yml and a directory called "files"
#### a. Ansible.cfg:- This is the brain and the heart of Ansible, the file that governs the behavior of all interactions performed by the control node.

#### b. Iventory:-the inventory is a list of managed nodes, or hosts, that Ansible deploys and configures. this inventory carries the ip address of the slave node in this project.

#### c. play-slave.yml:- the Ansible Playbook in this project contains the blueprint of automation tasks on the slave node, which are IT actions executed with limited manual effort, across an inventory of IT solutions.

#### d. files:- contains the file "lamp-slave.sh" which the playbook use to deploy laravel cloned from github repository only on the slave node. https://github.com/laravel/laravel.git


![Ansble-playbook](<snapshorts/installations of ansible playbook to slave.PNG>)

![ok=6](<snapshorts/continuation of ansible play book to slave.PNG>)

![Slave IP@192.168.30.21](<snapshorts/laravel page with slave ip adress.PNG>)


THANK YOU FOR YOUR TIME