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

![EC2_3](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/0bc42067-e793-4d0e-b72f-0d3b62f1e90e)

Under "Instance type" choose t2.micro
<br>
Under "Key pair (login)" choose your key pair that you already created(If you'd like to know how to create a key pair,check my repo "Host-a-wordpress-website-in-AWS" n0.7)
<br>
Under "Network settings",click edit 
<br>

![EC2_4](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/6514ab3b-cd9e-4599-af04-529c2bff34a6)




Under VPC choose the VPC we just created
<br>
Under Subnet,choose a private subnet
<br>
Under "Auto-assign public IP" leave at disable
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




