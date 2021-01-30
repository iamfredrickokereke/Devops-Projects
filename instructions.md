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

