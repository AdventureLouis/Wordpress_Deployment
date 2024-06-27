### Activate a Domain name for our ALB DNS name
<br>
I already registered a domain name on AWS,now to point our application load balancer DNS name we will need to create a record set on route  53
<br>

![Route53_1](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/cd6bc8e9-c33b-4841-9f2f-64db4fc24941)

On your AWS management console navigate to the search bar and typr route 53,once the route 53 is opened,click on the hosted zone to open it
<br>

![Route53_2](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/f70f24d0-c68e-471c-87c6-ac8f59b9fe58)

In the hosted zone page,check the boxes next to your domain name and click create record 
<br>

![Route53_3](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/e36db7a8-faa5-48a4-a8cf-7526c32763bc)

<br>
In the create record page,under record name,type "www"
<br>
Under "record type" choose "route traffic to an IPV4 and some AWS services
<br>
Under "Alias" toggle it to open
<br>
Under "route traffic to" choose "Alias to Application and classic load balancer"
<br>
Under "region" choose your region
<br>
Under "choose load balancer" click the empty box to choose your application load balancer
<br>
Under routing policy,choose simple routing and click create record
<br>

![Screenshot 2024-06-27 at 3 27 55 PM](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/7734a6d4-e0ae-4540-b930-60c9e2c927ad)

Now on a new tab start typing your domain name with www i.e www.lab-loui.org,and this will take your wordpress site same as before when we used the application load balancer DNS name
<br>

![Route53_6](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/0adff88f-006a-4e88-a54b-b01ab8cc8ce0)



Once last step is to register our DNS name on the wordpress admin,so on a new tab open with your domain name again this time add /wp-admin and this will take you to the admin page of your wordpress.
<br>
on the admin page of the wordpress,scroll on the left pane and click the following settings>General as seen above
<br>

![Route53_4](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/6cf2737e-4489-41ea-9675-0d5e5c7eac11)

Now go back to previous tab where you have your domain name and copy it as shown above
<br>
On the general page,scroll down to "Wordpress Address URL" and paste the the domain name you just copied
<br>

![Route53_6](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/3d3747b3-d380-403f-a08c-0d273d2e511d)

![Route53_7](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/10910b44-3f3d-429c-94ec-b46462d22318)
<br>

Above images are before and after pasting your new domain name into "Wordpress Address (URL) and "Site Address(URL)"
