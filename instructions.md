

# 
**Web stack-implementation(LAMP)**


 The goal of this project is to describe the concepts of Continuous Integration, Continuous Delivery / Deployment and DevOps on a Lamp web stack.


     Never heard about LAMP stack? No - Okay.


LAMP => LINUX


                 APACHE


                 MySQL


                 PHP


All together it's called a stack, just like you here some people say they are Mern  or Mean stack developers.


Mern => mongodb, express, reactjs and nodejs


Mean => mongodb, express, angularjs and nodejs


Pern => postgresqldb, express, react and nodejs


# Tldr;

#Video link

Prerequisites:



1. Aws account running an EC2 instance
2. Internet connection
3. Fundamental Knowledge of downloading and installing
4. Basics linux skills

 \
 \



# <span style="text-decoration:underline;">Implementation</span>



1. Open your PC browser and login to ** https://aws.amazon.com/**
2. A region is selected by default( change if necessary), from the search bar type **EC2** and click.
3. From the Ec2 dashboard, click on the button **“Launch instance**” to start using a virtual server.

    

<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")


4. An AMI window displays, type “ubuntu” on the search bar and hit enter, or scroll down to select “**Ubuntu Server 20.04 LTS (HVM), SSD Volume Type” based on your system architecture.**

                  note: the AMI(Amazon machine image) is always different from user to user



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")




5. The next step of configuring our EC2 is to select the **instance type**, preferably a** t2 micro - Freetier.** Then click (3) configure instance showing at the top **or** click next configuration details at the bottom.
6. To configure the instan

    

<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")


7. 

    **  **

1. 

 

ec2 - ubuntu 20 hvm pem -ppk use public ip on putty ubuntu user on ec2

Install Apache using Ubuntu’s package manager ‘apt’:

#update a list of packages in package manager $ sudo apt update #run apache2 package installation $ sudo apt install apache2

check service

$ sudo systemctl status apache2

open tcp port 80

check

$ curl [http://localhost:80](http://localhost/) or $ curl [http://127.0.0.1:80](http://127.0.0.1/)

get public ip - curl -s [http://169.254.169.254/latest/meta-data/public-ipv4](http://169.254.169.254/latest/meta-data/public-ipv4)

http://:80

$ sudo apt install mysql-server

$ sudo mysql_secure_installation

sudo mysql

mysql> exit

$ sudo apt install php libapache2-mod-php php-mysql

php -v

$ sudo mkdir /var/www/projectlamp

$ sudo chown -R $USER:$USER /var/www/projectlamp

$ sudo vi /etc/apache2/sites-available/projectlamp.conf

&lt;VirtualHost *:80> ServerName projectlamp ServerAlias [www.projectlamp](http://www.projectlamp/) ServerAdmin webmaster@localhost DocumentRoot /var/www/projectlamp ErrorLog ${APACHE_LOG_DIR}/error.log CustomLog ${APACHE_LOG_DIR}/access.log combined

$ sudo ls /etc/apache2/sites-available You will see something like this 000-default.conf default-ssl.conf projectlamp.conf

$ sudo a2ensite projectlamp

$ sudo a2dissite 000-default

$ sudo apache2ctl configtest

$ sudo systemctl reload apache2

sudo echo 'Hello LAMP from hostname' $(curl -s [http://169.254.169.254/latest/meta-data/public-hostname](http://169.254.169.254/latest/meta-data/public-hostname)) 'with public IP' $(curl -s [http://169.254.169.254/latest/meta-data/public-ipv4](http://169.254.169.254/latest/meta-data/public-ipv4)) > /var/www/projectlamp/index.html

http://:80

http://:80

sudo vim /etc/apache2/mods-enabled/dir.conf

#Change this: #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm #To this: DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm

$ sudo systemctl reload apache2

$ vim /var/www/projectlamp/index.php
