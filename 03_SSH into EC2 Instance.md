#### SSH into the EC2 Instance from Terminal

![DIagram_Architecture](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/6af2c1b9-371a-4aa5-a6ef-230b45f6f6be)

##### For MAC/Linux users
<br>
In order for you to be able to successfully ssh into your ec2 instance from your personal computer or server,you first need to ensure that you know where your primary key pair
from  AWS is saved on your computer


as shown above,lets assume your primary key pair is saved in your document directory after opening your terminal first navigate to your document directory and type:
```bash
chmod 400 "demoEC2key.pem"
```

![EC2_9](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/07ca6ecb-e4d5-4124-98f0-ee04433f6838)



* chmod 400 "demoEC2key.pem"  --> This command will help change file permissions for "4" for owner "0" for group and "0" for others
  without setting the permission with the command "chmod 400 "demoEC2key.pem" " you cannot ssh into the ec2 instance 
  <br>
  
ssh -i "demoEC2key.pem" ec2-user@IPV4_Public_Address.region

