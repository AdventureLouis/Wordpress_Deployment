### Launch EC2 instance using Amazon Linux 2(AL2)

![DIagram_Architecture](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/f27b9186-75fd-4ce5-85ab-68372a9c5959)

In this project we will be hosting the wordpress website with the help of LAMP(Linux,Apache,Mysql and PHP) services and before we can the LAMP services we first need to launch an EC2 instance
<br>
#### Begin  Launch of EC2 instance 

![EC2_1](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/4a366e10-2176-4ce9-9aa3-7580ba4caf65)

To begin the launch of EC2 instance,open your AWS managment console on the search bar type EC2,on the EC2 page click launch instance as seen above
<br>

![EC2_2](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/6c33aaeb-1c1b-4ff3-b472-f5d9add94ba8)
Under name type the name of your ec2 instance as 
<br>
Under Application and OS Images (Amazon Machine Image),type Amazon linux
<br>
Under Amazon Machine Image (AMI),choose "Amazon Linux 2 AMI(HVM) - Kernel 5.0,SSD Volume Type" as seen above
<br>

![EC2_3](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/a4dba929-fa95-4833-aedc-bf98c20d901d)


Under "Instance type" choose t2.micro
<br>
Under "Key pair (login)" choose your key pair that you already created(If you'd like to know how to create a key pair,check my repo "Host-a-wordpress-website-in-AWS" n0.7)
<br>
Under VPC choose the VPC we just created
<br>
Under Subnet,choose a public subnet
<br>
Under "Auto-assign public IP" set it to disable because we will be launching the ec2 in private subnet
Under "Network settings",click edit 
<br>

![EC2_4](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/6856bd1c-2184-45e7-b1c4-8efc6335b6f6)


<br>
Under "Firewall (security groups)",select create security group 
<br>
Under name of a security group,give a name to your security group
<br>
Under "Description" you can use same name as name of security group
<br>
Under "Inbound Security Group Rules",set Type to "SSH",set protocole to "TCP",set port range to "22"
<br>
Under "Source type" choose "My IP"
<br>

![EC2_5](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/027e60cd-22f0-477a-8717-932dce7fd409)
After creating the EC2 instance you can see above that it is successfully created
<br>

![EC2_6](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/9e1563bf-ef0f-46f5-9c05-5ce11cb84f69)


To ensure that your newly launched EC2 is ready to use,make sure under "Instance state" its showing "Running" and under "status-check" its showing "2/2 checks passed" and this can be seen highlighted above

#### Configure Resource Group
<br>
Its time to add more configuration to the resource we creating when we where creating the EC2 instance
<br>
The configuration will be adding HTTP on port 80 and HTTPS on port 443
<br>

![EC2_10](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/f1406b59-79eb-4153-ba5c-ca9e10f104d0)

To achieve this,check on the box next to your ec2 instance and under security tab you will see the security group we created now click to open it
<br>

![EC2_11](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/e54db8b3-eaad-45ae-a5d4-2abb638285a0)

Now its open,click on "Edit inbound rules" as seen above,we want to add more rules so our ec2  can be able to access the internet on port 80 etc 
<br>

![EC2_12](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/6ff0216b-ef68-4162-826d-8554483edde1)


Click add rule and under "Type" choose HTTP,under "Protocole" choose "TCP",under "port range" choose 80,under "source" choose anywhere-IPV4
<br>
Again Click add rule and under "Type" choose HTTPS,under "Protocole" choose "TCP",under "port range" choose 443,under "source" choose anywhere-Ipv4 and finally click save rules


