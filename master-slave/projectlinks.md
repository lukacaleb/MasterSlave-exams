https://medium.com/@melihovv/zero-time-deploy-of-laravel-project-with-ansible-3235816676bb

https://www.cherryservers.com/blog/how-to-install-and-setup-postgresql-server-on-ubuntu-20-04

https://dev.to/sureshramani/how-to-deploy-laravel-project-with-apache-on-ubuntu-36p3

https://docs.ansible.com/

lamp.sh
# # Update the system
# sudo apt update
# sudo apt upgrade -y


# # Install LAMP stack
# # sudo apt install -y apache2 mysql-server php libapache2-mod-php php-mysql

# sudo apt-get install software-properties-common 

# sudo apt-get install apache2 -y

# sudo apt-get install mysql-server -y

# sudo apt-get-repository -y ppa:ondrej/php

# sudo apt-get update 

# sudo apt-get install libapache2-mod-php php php-common php-xml php-mysql php-gd php-mbstring php-tokenizer php-json php-bcmath php-curl php-zip unzip -y

# # Install composer on ubuntu 
# sudo apt-get update
# sudo apt-get install git composer -y
# cd /var/www/html
# # git clone https://github.com/laravel/laravel.git .
# # composer install


# # Clone the PHP application from GitHub
# # git clone https://github.com/yourusername/yourphpapp.git /var/www/html/yourphpapp
# cd /var/www/html
# git clone https://github.com/laravel/laravel.git .
# # composer install

# #Deploying a new laravel project
# # cd /var/www/html
# # composer create-project --prefer-dist laravel/laravel .
# # cd /var/www/html
# # cp .env.example .env
# # php artisan key:generate

# # Configure Apache virtual host
# # sudo tee /etc/apache2/sites-available/yourphpapp.conf <<EOF

# cat << EOF > /etc/apache2/sites-available/laravel.conf
# <VirtualHost *:80>
#     ServerAdmin calebluka@gmail.com
#     DocumentRoot /var/www/html/laravel/public
#     ServerName 192.168.20.10

#     <Directory /var/www/html/laravel>
#     Options Indexes Multiviews FollowSymLinks
#     AllowOveride All
#     Require all granted
#     </Directory>

#     ErrorLog \${APACHE_LOG_DIR}/error.log
#     CustomLog \${APACHE_LOG_DIR}/access.log combined
# </VirtualHost>
# EOF

# sudo a2emod rewrite
# sudo a2ensite laravel.conf
# sudo systemctl restart apache2



# # Configure MySQL (you may need to set a root password)
# sudo mysql -u root -e "CREATE DATABASE yourdb"
# sudo mysql -u root -e "GRANT ALL ON yourdb.* TO 'youruser'@'localhost' IDENTIFIED BY 'yourpassword'"




vagrant.sh

# vagrant init ubuntu/trusty64

# cat <<EOF > Vagrantfile
# Vagrant.configure("2") do |config|

#   config.vm.define "slave" do |slave|

#     slave.vm.hostname = "slave"
#     slave.vm.box = "ubuntu/trusty64"
#     slave.vm.network "private_network", ip: "192.168.30.21"

#     slave.vm.provision "shell", inline: <<-SHELL
#     sudo apt-get update && sudo apt-get upgrade -y
#     sudo apt install sshpass -y
#     sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config
#     sudo systemctl restart sshd
#     sudo apt-get install -y avahi-daemon libnss-mdns
#     SHELL
#   end

#   config.vm.define "master" do |master|

#     master.vm.hostname = "master"
#     master.vm.box = "ubuntu/trusty64"
#     master.vm.network "private_network", ip: "192.168.30.20"

#     master.vm.provision "shell", inline: <<-SHELL
#     sudo apt-get update && sudo apt-get upgrade -y
#     sudo apt-get install -y avahi-daemon libnss-mdns
#     sudo apt install sshpass -y
#     sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config
#     sudo systemctl restart sshd
#     SHELL
#   end

#     config.vm.provider "virtualbox" do |vb|
#       vb.memory = "1024"
#       vb.cpus = "2"
#     end
# end
# EOF

# vagrant up

# source lamp.sh 


playbook.yml

<!-- ---
- name: Deploy LAMP Stack
  hosts: Slave
  become: yes

  tasks:
    - name: Copy the script to the Slave node
      copy:
        src: install_lamp.sh
        dest: /tmp/install_lamp.sh

    - name: Execute the bash script
      shell: /bin/bash /tmp/install_lamp.sh -->

