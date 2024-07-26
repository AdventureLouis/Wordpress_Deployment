
![System_Achitecture](https://github.com/user-attachments/assets/1988fdc1-0a5f-41da-9d4a-d0cf907754a1)


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

![ALB14](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/25092f82-090c-4de8-94f2-c7da4c638e2f)

<br>
Under "Security Group" here we need to create a new security group that will route traffic from anywhere
<br>
In creating a new security group,we give a name to the new security group
<br>
Under inbound rules for the new security group,set type to HTTP,protocol to TCS,port to 80  and source to anywhere
<br>

![ALB24](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/c7495440-021a-4e73-8b93-c25e2ccd74b2)

Still under inbound rule,click add rule again,set type to HTTPS,protocol to TCP,port to 443 as shown above
<br>
Under "Listener" for protocol choose "HTTP",for "port" choose 80
<br>
![ALB7](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/186d5a19-c232-4142-bbd3-6d1074912a6f)
<br>
Under "Default action" choose create target group
<br>
Now its time to create a target group in a new tab,under choose target type,select "instances"
<br>

![ALB8](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/c692e5a8-3f9c-4751-8b9d-c696e4af10ae)

Under target group name,give a name to your target group
<br>
Under "Protocol : Port",choose HTTP and port 80
<br>
Under "IP address type" choose IPV4 
<br>
Under VPC,choose the VPC we previously created
<br>
Under "Protocol version" choose HTTP1
<br>

![ALB9](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/4f4e8eaa-b359-4720-9088-197a807db271)
![ALB10](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/b145490e-239f-423a-a778-e8af8f83ff87)

Under "health checks" for health check protocol,leave it at http
<br>
Under "Health check protocol" leave it at default
<br>
Under "Advanced health check settings" scroll down until you get to "Success codes" and leave it at 200 and 302,this is because 200 and 302 can be success codes
<br>

![ALB15](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/5910929f-dab7-41f7-959f-1731110f3dd7)
![ALB16](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/96630ddf-a86d-4ce5-9de8-e18014465338)

<br>
Click next
<br>
Under "Register targets" check the boxes next to the private ec2  instance and click "Include as pending" as shown above and click create target group

![ALB17](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/633e8d63-01f7-4a3c-8427-e30613f96ef1)

<br>
Now that we have successfully created a new target group
<br>
We can now go back to the Application load balancer creation page select a target group under "Listeners and routing" and click on refresh icon next to select a target group
<br>
Now click on the drop-down arrow and select the new target group you just created scroll down and click create load balancer

![ALB18](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/e37761e2-e2e7-497d-a963-602c7c718010)

![ALB19](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/6093be8c-12f2-43de-8345-16c7affd83fb)

Now that we have successfully created the application load balancer,its time open our wordpress server
<br>
Navigate to your load balancer,check on the box next to the load balancer and under Details copy your DNS name and paste it on a new tab
to open the wordpress page for the first time
<br>

![ALB20](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/54f0e455-484a-48b6-bf92-e1da87e1c73c)
<br>
Once the wordpress page is open ,click  continue
<br>
Fill in all neccessary information of your site and click install wordpress
<br>
![ALB21](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/2822b1e9-bbec-4530-a43e-4821a0103d8c)
![ALB22](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/bbdf711d-d515-4500-9abd-e046258311ec)
<br>
Now add /wp-admin next to the url name and you will be prompted to input your password and click login
<br>
Now we have successfully loged into our wordpress site admin page as seen above
