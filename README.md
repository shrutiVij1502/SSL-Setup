# POC 1

###  Create an EC2 server
### Install Nginx in it
### Create a sample index.html page and deploy it on that Nginx server
### Configure domain and apply SSL, Configure automation script for SSL renewal.


**Step1 : Create an EC2 Instance**

Login to AWS Management Console and open EC2 service.
You can either go to Services -> Compute -> EC2
or type EC2 in the search bar and hit enter. Once you see EC2 option click on that.
This will lead you to EC2 dashboard like below.
To Create EC2 Instance in AWS, Click Launch Instance
Choose an Amazon Machine Image (AMI) to start your OS , Once you click on Launch Instance, you will be presented with a 7 step configuration screen, for now we will remain the things same as default.

Create/Select a Key Pair - Select Create a new key pair option – > name your key pair -> Download Key Pair -> Launch Instance , Download keypair and click Launch Instances
Scroll down the page and click on View Instances, You will see like below

![image](https://user-images.githubusercontent.com/67600604/171338086-a56c4cbd-a8f0-439e-9685-ba2dcd10361b.png)

**Step2 : Install Nginx in it**

Connect your Instance with putty with the key we have downloaded at the time of launching the instance.

![image](https://user-images.githubusercontent.com/67600604/171338471-18328e62-3a3c-4a40-a056-3993fa5f179b.png)

In our case, we are using AMI Linux. so , for installing nginx we will use the yum commands

sudo yum install nginx

sudo systemctl start/status/stop nginx - to start stop and check status of the nginx server

**Step3 : Create a sample index.html page and deploy it on that Nginx server**

Now, go into the file location /usr/share/nginx/html folder and create a file named as index.html. Now restart the nginx server and search for the public ip in your local browser and you will be able to see your page of index.html file 

![Screenshot (176)](https://user-images.githubusercontent.com/67600604/171344033-2d60f166-dad6-4e17-ae76-e4e4eac7956e.png)

**Step4 : Configure domain and apply SSL, Configure automation script for SSL renewal.**

To Configure the domain, we have to  purchase the domain. In our case,I have taken free domain name from the freenom.com, i.e. shruti1.ga
Sign in to freenom.com and there is a service named as Route53 in amazon we will create hosted zone ther and will get 4 nameservers there, have to add those nameserver ther in the freenom DNS settings to make it connected with the IP address. Create record in the hosted zone and set the TTL there to update it after the given time period. In our case, I have assigned 60 seconds 

![image](https://user-images.githubusercontent.com/67600604/171350944-ca6ddd3f-75fe-4e6c-bd52-730d7e93ea16.png)
the above screenshot has the 4 nameservers ofour Route 53 hosted zone 

![Screenshot (183)](https://user-images.githubusercontent.com/67600604/171348628-45592558-1875-4999-bc8f-cd7c7f48eafe.png)

Now, to apply and configure SSL , 

sudo yum install certbot python3-certbot-nginx

Confirming the domain - sudo vim /etc/nginx/nginx.conf, it should be in this pattern

server_name shruti1.ga www.shruti1.ga;

Then save the file, quit your editor, and verify the syntax of your configuration edits: sudo nginx -t and then sudo systemctl reload nginx

Obtaining an SSL Certificate - sudo certbot --nginx -d shruti1.ga -d www.shruti1.ga -> This runs certbot with the --nginx plugin, using -d to specify the domain names we’d like the certificate to be valid for.

![Screenshot (186)](https://user-images.githubusercontent.com/67600604/171350638-114aae9a-74ec-4487-a3a1-7f74ac2dab88.png)

You can see here now it is https://shruti1.ga

![Screenshot (184)](https://user-images.githubusercontent.com/67600604/171350740-47048d96-9638-462a-884a-ff2a7905306a.png)






 
 
 
 



