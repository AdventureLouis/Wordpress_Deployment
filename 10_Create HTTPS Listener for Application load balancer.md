#### Create HTTPS Listener for our Application load balancer
The essence for creating HTTPS listener is to add an extra layer of seurity to our wordpress site
<br>
To configure the HTTPS,on your AWS management console,navigate to the search bar and type EC2,on the left pane of the EC2 page,under "Load Balancing" select "Load Balancer"
<br>

![ALB23](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/d44533f1-ad13-4a3a-a27f-f7062fe8576b)
<br>
On the load balancer page,check the box next to the application load balancer 
<br>
Click on "Listener and rules" tab and click add Listener
<br>

![HTTPS1](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/cfc37f45-7e25-4f07-acce-3351fbd8d7e1)

In add listener page,under "Protocol" Type HTTPS and under "port" type 443
<br>
Under "Authentication" no need to check the box
<br>
Under "Routing Actions" choose "Forward to target groups"
<br>
Under "Target group" select the target group we previously created
<br>

![HTTPS2](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/1205b902-38ed-4ea0-a019-e131e1c38518)

Under "security category" choose "all security policies"
<br>
Under "Certificate source" there are 3 options and I will be choosing ACM(Aws certificate manager),I discussed how you can create ACM in #10
<br>
Under "certificate from ACM" choose your ACM certificate you previously created in #10
<br>
and click add
<br>

Now that we have add listener we now need to go back to our load balancer and redirect the already existing http with port 80 to https with port 443,to do this go back to your application load balancer
<br>

![HTTPS4](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/9e5b65a5-480d-4984-952f-818cf04c35f1)
<br>
While in your application load balancer under "Listeners and rules",check the box next to "HTTPS:80" and click on the drop-down next to 
manage listener and select edit listener as shown above
<br>

![HTTPS5](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/06304e22-1711-4ff2-a327-814fe4a4d596)
<br>
On the Edit listner page,under "listener configuration" leave protocol and port at default with http and 80
<br>
Under default actions select "Redirect to URL"
<br>
![HTTPS6](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/b7040a91-bc7f-4374-9717-e4c6e0bbe38d)
<br>
Under protocol leave it at HTTPS and under port type 443 and click save changes
<br>

![HTTPS7](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/e3da42c6-76c4-43ed-8fc5-0826209cccca)
<br>
Now we can see our protocolsn are working fine as seen above
<br>

![HTTPS8](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/cbf77c6a-25c2-4570-bd23-eb68e112af29)

We can now retype the wordpress site with "https://www.lab-loui.org/" as seen above and so our website is now secured
<br>

![HTTPS9](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/2d0cda74-9afc-421f-9fb1-18a953119148)
<br>
One last step now is to ensure we register our https in the wordpress admin and to achieve this just type /wp-admin after the domain name
as seen above
<br>

So now we are in the admin page,scroll down on the left pane and select settings>General and 
