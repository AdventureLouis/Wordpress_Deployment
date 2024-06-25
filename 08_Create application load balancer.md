
![DIagram_Architecture](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/4d507402-aac6-4234-bb14-6a8867e7bc06)
<br>
### Create and configure Application load balancer(ALB)
<br>
Through the application load balancer the user can interact with bastion ec2 in the public subnet,that is the bastion ec2 instance will only accept traffic from the application load balancer.
<br>
The application load balancer is a service that is managed by AWS for distributing traffic between targets.
<br>
#### Application load balancer installation
<br>

![ALB1](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/69923327-bd7e-4630-badd-7726f7805624)

To begin the installation of Application load balancer,on your AWS management console navigate to the search bar and type EC2,on the ec2 page scroll down on the left panel until you see
"Load Balancing" and click "Load Balancers" under Load balancing as shown above
<br>

![ALB2](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/2bbc42f7-05f9-4a8d-abd2-6626bdb85c49)

On load balancers page,click on "Create load balancer" as shown above
<br>

![ALB3](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/efb2fde9-14d8-46fa-a4a0-836145853245)

Under "Compare and select load balancer type" choose "Application load balancer"  on the left part and click "create" as shown above
<br>

![ALB4](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/935c86a3-a1d4-458b-b16b-1ef3cc9c0b44)


A page for creating the application load balancer is now open and you need to start creating
<br>
Under "Load balancer name" give a name to your ALB
<br>
Under "Scheme" select "internet facing"
<br>
Under "IP address type" select "IPV4"
<br>

![ALB5](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/95864426-7541-4871-a82a-dd431ef26d5c)

Under "VPC" select the VPC we previously created
Under "Network mapping" choose the 3 public subnets
<br>

Under "Security Group" choose the Bastion SG
