## These are steps to implement this project

ec2 - ubuntu 20 hvm
pem -ppk
use public ip on putty
ubuntu user on ec2

Install Apache using Ubuntu’s package manager ‘apt’:

#update a list of packages in package manager
$ sudo apt update
#run apache2 package installation
$ sudo apt install apache2

check service


$ sudo systemctl status apache2

open tcp port 80

check

$ curl http://localhost:80
or
$ curl http://127.0.0.1:80

get public ip - curl -s http://169.254.169.254/latest/meta-data/public-ipv4

http://<Public-IP-Address>:80   

$ sudo apt install mysql-server

$ sudo mysql_secure_installation



sudo mysql

mysql> exit

$ sudo apt install php libapache2-mod-php php-mysql

php -v

$ sudo mkdir /var/www/projectlamp

$ sudo chown -R $USER:$USER /var/www/projectlamp

$ sudo vi /etc/apache2/sites-available/projectlamp.conf

<VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


$ sudo ls /etc/apache2/sites-available
You will see something like this
000-default.conf  default-ssl.conf  projectlamp.conf

$ sudo a2ensite projectlamp

$ sudo a2dissite 000-default

$ sudo apache2ctl configtest

$ sudo systemctl reload apache2

sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html


http://<Public-IP-Address>:80

http://<Public-DNS-Name>:80


sudo vim /etc/apache2/mods-enabled/dir.conf

<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>


$ sudo systemctl reload apache2

$ vim /var/www/projectlamp/index.php

<?php
phpinfo();


$ sudo rm /var/www/projectlamp/index.php



