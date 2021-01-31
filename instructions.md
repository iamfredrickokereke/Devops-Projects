Web stack-implementation(LAMP)
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
 
Tldr;
#Video link


Prerequisites:
Aws account running an EC2 instance
Internet connection
Fundamental Knowledge of downloading and installing
Basics linux skills




Implementation
Open your PC browser and login to  https://aws.amazon.com/
A region is selected by default( change if necessary), from the search bar type EC2 and click.
From the Ec2 dashboard, click on the button “Launch instance” to start using a virtual server.
An AMI window displays, type “ubuntu” on the search bar and hit enter, or scroll down to select “Ubuntu Server 20.04 LTS (HVM), SSD Volume Type” based on your system architecture.
 
                  note: the AMI(Amazon machine image) is always different from user to user
 
 
The next step of configuring our EC2 is to select the instance type, preferably a t2 micro - Freetier. Then click (3) configure instance showing at the top or click next configuration details at the bottom.
