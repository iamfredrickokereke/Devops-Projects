Simple To-Do application on MERN Web Stack
 

The goal of this project is to describe the concepts of Continuous Integration, Continuous
Delivery / Deployment and DevOps on a Lamp web stack.
 Never heard about Mern stack? No - Okay.
 


 

Tldr;
#Video link

Prerequisites:
•	Aws account running an EC2 instance
•	Internet connection
•	Fundamental Knowledge of downloading and installing
•	Basics Linux skills

Implementation

•	Open your PC browser and login to https://aws.amazon.com/

•	A region is selected by default (change if necessary), from the search bar type EC2 and click.

 
 
•	From the Ec2 dashboard, click on the button “Launch instance” to start using a virtual server.


 

•	An AMI window displays, type “Ubuntu” on the search bar and hit enter, or scroll down to select “Ubuntu Server 20.04 LTS (HVM), SSD Volume Type” based on your system architecture.
                 
  Note: the AMI (Amazon machine image) is always different from user to user

 
 
 
•	The next step of configuring our EC2 is to select the instance type, preferably a t2 micro - Free tier. Then click (3) configure instance showing at the top or click next configuration details at the bottom.
 
  
Move to next step
 
 
•	To configure the instance, we will leave all default but scroll to the bottom and on the advanced details section, in the user data column add below script as shown on the screenshot.
  
 
 






Move to next step
  
 
 
 
•	Move to tab 5 to Add tags to our EC2 instance, I have deliberately skipped tab 4 to choose the default storage volume given by AWS.
 
Tags are key-value paired fields and help to categorize your AWS resource, now click ADD TAG to assign a unique name and move to next.
 
 
 Move to Next
 
•	We will not modify the default security group, but go with the default console access via ssh on port 22.
 Reason:  The security Group are set of firewall rules which denies and grant access to our EC2 instance, 
To access the EC2 instance with a console, we use mobaxterm as shown below
 
 
  Move to Next
Concluding our Ec2 setup,

 
 
•	Click review and launch
 
  
You will get a Prompt to Create a Private Key File, feel free to choose an existing one, if it already exists on the same PC.
 
Download the key file to a good location, to be used later, Then Launch.
 
  
Done? Good Job, let’s get to business now.
 
 
Copy your own Public IP as shown on the above screenshot, nowit’s time to use the console 
Yay!!!

Now, Open mobaxterm to connect the Ec2 instance with the public ip shown above, 

 

 
You have now connected to the EC2 instance via SSH
Type clear, to have a neat console and proceed.
We will now check if our userdata scripts were loaded.


 



 By default EC2 user is given sudo privilege



Great!!!



Application Code Setup

We have our Linux instance up and nodejs installed, let's setup the code for our project.
Run this code:



 
Install ExpressJs
Express is a framework for Node.js,  which helps to define routes of your application based on HTTP methods and URLs.
To use express, we need to install it using npm as shown below:

Run this code:



 
Great MYSQL is installed and configured for use, we could test by running below code:



 

Now we have create the file, let's Install the dotenv module to store our environmental variables


 
Now let's add some code for our project into app.js file created earlier
 
 

Copy and paste below code:

 





















Remember to press save and exit -  "  :wq " 
 

Notice that we have specified to use port 5500 in the code. This will be required later when we go on the browser. 
Result to confirm above script, run


 

Excellent!!!
Now we need to open this port on our Security Group by editing the inbound rule as shown below:
 

Let's check the browser now and confirm it runs on port 5500 using the ip or DNS name.
 


Routes
There are three actions that our To-Do application needs to be able to do:

•	Create a new task
•	Display list of all tasks
•	Delete a completed task

Each task will be associated with some particular endpoint and will use different standard HTTP request methods or sometimes called HTTP verbs :
 POST (Create task),
 GET (Read tasks by id),
 DELETE ( Remove task by id)

For each task, we need to create routes that will define various endpoints that the To-do app will depend on.  A simple route can be represented as  " /route" 
So let us create a folder, navigate to it and create a file  to store all routes




 



 



Models
Now comes the interesting part, since the app is going to make use of Mongodb which is a NoSQL database, we need to create a model.

A model is at the heart of JavaScript based applications, and it is what makes it interactive.

We will also use models to define the database schema . This is important so that we will be able to define the fields stored in each Mongodb document.

To create a Schema and a model, we will install mongoose which is a Node.js package that makes working with mongodb easier.

Change directory back Todo folder with cd .. and install Mongoose







Run below command:
 


Type “Is” without the quotes to confirm the file was created

 
 
















Now we need to update our routes from the file  api.route.js in ‘routes’ directory to make use of the new model.
In routes directory, delete the code inside with :%d command and paste there code below into it then save and exit

 






















 

Good Job!

MongoDB Database

We need a database where we will store our data. For this we will make use of mLab. mLab provides MongoDB database as a service solution (DBaaS), so to make life easy, you will need to sign up for a shared clusters free account, which is ideal for our use case. Sign up here. Follow the sign up process, select AWS as the cloud provider, and choose a region near you.
We need to tell apache to enable this new directory to serve our site and disable the default site directory:
 
 
Run this code to store our environment variable file

 



Remember to get your dbname, username and password to update your .env file

 
Check the .env file using  this command as shown "  ls -lra "
 
Now we need to update the index.js to reflect the use of .env so that Node.js can connect to the database.






 Simply delete existing content in the  app.js file, and update it with the entire code above, and the result is below.
 


Testing Backend Code without Frontend using RESTful API

We will be using Postman to test all the API endpoints and make sure they are working. For the endpoints that require body, we will return JSON back with the necessary fields. 
 
We will add a raw content to the body, with the help of the body parser to generate a new todo.

See below output:

POST METHOD
 

GET METHOD
 




DELETE METHOD
 


Frontend creation

we are done with the functionality we want from our backend and API, it is time to create a user interface for a Web client (browser) to interact with the application via API. To start out with the frontend of the To-do app, we will use the create-react-app command to scaffold our app.
In the same root directory as your backend code, which is the Todo directory, run:



This will create a new folder in your Todo directory called client, where you will add all the react code.
 


Next we run below code:


Now edit the package.json file with below:








Configure Proxy




Add the key value pair in the package.json file "proxy": "http://localhost:5500"
Check the browser 
 






Creating your React Components





Inside input.js file















To make use of Axios, which is a Promise based HTTP client for the browser and node.js, you need to cd into your client from your terminal and run yarn add axios or npm install axios.













































Delete the logo and adjust our App.js to look like this.
Move to the src folder












In the src directory open the App.css 












































Edit index.css and add above code, next navigate to the todo directory and run



Then refresh and check your browser.

You should get above output  when you visit the browser - simple To-Do and deployed to MERN stack

Hope this was informative.

PS: Remember to terminate your EC2 instance.
 
