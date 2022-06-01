# Create an EC2 server,Install Nginx in it, Create a sample index.html page and deploy it on that Nginx server, Configure domain and apply SSL, Configure automation script for SSL renewal.
Step1 : Create an EC2 Instance 

Login to AWS Management Console and open EC2 service.
You can either go to Services -> Compute -> EC2
or type EC2 in the search bar and hit enter. Once you see EC2 option click on that.
This will lead you to EC2 dashboard like below.
To Create EC2 Instance in AWS, Click Launch Instance
Choose an Amazon Machine Image (AMI) to start your OS , Once you click on Launch Instance, you will be presented with a 7 step configuration screen, for now we will remain the things same as default.

Create/Select a Key Pair - Select Create a new key pair option – > name your key pair -> Download Key Pair -> Launch Instance , Download keypair and click Launch Instances
Scroll down the page and click on View Instances, You will see like below

![image](https://user-images.githubusercontent.com/67600604/171338086-a56c4cbd-a8f0-439e-9685-ba2dcd10361b.png)

Step2 : Install Nginx in it

Connect your Instance with putty with the key we have downloaded at the time of launching the instance.

![image](https://user-images.githubusercontent.com/67600604/171338471-18328e62-3a3c-4a40-a056-3993fa5f179b.png)
In our case, we are using AMI Linux. so , for installing nginx we will use the yum command 

sudo yum install nginx

sudo systemctl start/status/stop nginx - to start stop and check status of the nginx server

Step3 : Create a sample index.html page and deploy it on that Nginx server

Now, go into the file location /usr/share/nginx/html folder and create a file named as index.html. Now restart the nginx server and search for the public ip in your local browser and you will be able to see your page of index.html file 

![Screenshot (176)](https://user-images.githubusercontent.com/67600604/171344033-2d60f166-dad6-4e17-ae76-e4e4eac7956e.png)

Step4 : Configure domain and apply SSL, Configure automation script for SSL renewal.

 



