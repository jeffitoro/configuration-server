# configuration-server

#### → SSH


# Presentation Me

# SFTP vs SSH

# What do we need our ?
- servername / servercloud / serverweb → applications (lamp) / database / php

# Understand Mecanisme / IMG
- Client → Server _ Server ← Client

# where do find it ?
	1. godaddy, one.com, google
	2. servercloud - data sur le disque - herbergeur

# security new user
adduser jeff

# mode sudo user
usermod -aG sudo jeff

# sync files keys ssh
rsync --archive --chown=jeff:jeff ~/.ssh /home/jeff

# ssh open
sudo ufw status

# exit + connexion new user

# update system 
sudo apt update && sudo upgrade

# installation webserver
sudo apt install apache2 apache2-utils

# verify installation
sudo systemctl status apache2
go to ip droplet 127.0.1.0

# www-data → groups activation
sudo chown www-data:www-data /var/www/html/ -R
sudo usermod -aG www-data jeff

# database
sudo apt install mysql-server
sudo mysql_secure_installation	// enter root root

# test database
sudo service mysql status
sudo mysql -u root -p and create database test;


# communication php
sudo apt install php libapache2-mod-php php-mysql
sudo apt install php libapache2-mod-php php-mbstring php-xmlrpc php-soap php-gd php-xml php-cli php-zip php-bcmath php-tokenizer php-json php-pear


# configuration fichiers apache2
sudo vim /etc/apache2/mods-enabled/dir.conf //priorité de lecture
sudo service apache2 restart
	- info.php phpinfo();

# next step laravel
	- install composer doc: Download Composer
	- mv composer.phar /usr/local/bin/composer
	- sudo apt install composer
	- install laravel
	- sudo chown -R $USER .composer/
	- export PATH=$HOME/.composer/vendor/bin:$PATH // path dans config
	- sudo rm -rf ~/.composer/cache/
	- sudo apt update && sudo apt install wget php-cli php-zip unzip curl
	- composer global require laravel/installer
	- run zip /* → scp server
	- sudo chown www-data: html/ -R

# apache2
sudo a2enmod rewrite

#virtualhost
<VirtualHost *:80>
        ServerName test2.molengeek.com
        DocumentRoot /var/www/html/test2/public

        <Directory /var/www/html/test2>
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/site-a_error.log
        CustomLog ${APACHE_LOG_DIR}/site-a_access.log combined
</VirtualHost>
sudo a2ensite test2.conf

#sudo systemctl restart apache2

