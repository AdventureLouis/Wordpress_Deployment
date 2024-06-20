### VPC Deployment in three Availabilty zones
<br>
In this course I will be utilizing AWS Management console,so open your amazon management console click on the search bar and type VPC,
and when the VPC page opens,click on "VPC and more",by clicking VPC and more you will be able to create VPC and many other resources such as public and private subnets,route-tables etc
<br>

![VPC1](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/e397c27a-4162-4a40-8b19-1931357f12c9)
<br>
Under "Auto-generate" type the name of your project(Louis-Project2),and note that the name you choose will be associated with every other resources that is created alonside VPC.
<br>
Under "IPv4 CIDR block" leave it at 10.0.0.0/16
<br>
under "IPv6 CIDR block" check the box No IPv6 CIDR block
<br>
Under "Tenancy" choose default
<br>

![VPC2](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/36525bc0-9149-41ae-947b-3ba194ddab59)

Under "Number of Availability Zones (AZs)" choose 3 and this is because we are trying to create  our resouces in 3 availability zones
<br>
Under "Number of public subnet" choose 3
<br>
Under "Number of private subnet" choose 3
<br>
Under "NAT gateways ($)" choose "in 1 AZ" the reason we have decided to choose this option is to reduce cost thereby having a nat gate only in one availability zone and it will be shared by resources in other availabilty zones and also note that nat gateway is only associated to the private subnets while the internet gateway(IGW) is associated to the public subnets.
<br>
Under "VPC endpoints" choose None  and this because for now we dont need s3 bucket endpoint.Finally click create vpc
