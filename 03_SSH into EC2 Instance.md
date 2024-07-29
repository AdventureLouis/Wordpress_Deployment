#### SSH into the EC2 Instance from Terminal

![System_Architecture_By_Louis](https://github.com/user-attachments/assets/7e4ac40f-8db6-4aa6-a8a8-391ce989d0e9)


##### For MAC/Linux users
<br>
In order for you to be able to successfully ssh into your ec2 instance from your personal computer or server,you first need to ensure that you know where your primary key pair
from  AWS is saved on your computer
<br>


![EC2_9](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/07ca6ecb-e4d5-4124-98f0-ee04433f6838)

### SSH into Bastion ec2(Server)
<br>
Because we want to provide an extra layer of security,we will first ssh into the Bastion server then from the Bastion ssh into our ec2 instance that is in the private subnet
<br>
Lets assume your primary key pair is saved in your document directory, after opening your terminal first navigate to your document directory and type:

```bash
chmod 400 "demoEC2key.pem"
```

* chmod 400 "demoEC2key.pem"  --> This command will help change file permissions for "4" for owner "0" for group and "0" for others
  without setting the permission with the command "chmod 400 "demoEC2key.pem" " you cannot ssh into any  ec2 instance 
  <br>
so after running above command in the terminal directory where you have your primary key pair(.pem key) saved,the next command we will run is
below

```bash
ssh -i "demoEC2key.pem" ec2-user@ec2-54-154-184-132.eu-west-1.compute.amazonaws.com
```
<br>
From above code the "2-54-154-184-132" is my public IPV4 of the Bastion server so just replace that with your own IPV4
<br>
Note that after running the code you will get a prompt message asking if you wish to continue,just type yes and diagram shown below
<br>

![EC2_16](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/a94210b1-f288-4b1c-8c9a-6750c646fb35)
<br>

### SSH into the EC2 Instance
So now its time to ssh into the EC2 instance from the bastion server and to achieve this,type "exit" to exit from the bastion server
<br>
Now in order to be able to ssh from he bastion into the ec2 private server we need the primary key pair(demoEC2key.pem) in our directory to also be in bastion server
<br>
So after exit to the directory where you have the keypair stored,type below code

```bash
cat demoEC2key.pem
```
The above command will open your primary keypair you should copy  till where you have %(dont copy the % symbol) 
Image below👇 

![EC2_17](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/bef6f47e-5f94-4e7e-b1b8-5af55c4bc0b5)
<br>
Next after copying the primary key pair,ssh back into the bastion server with the command below

```bash
ssh -i "demoEC2key.pem" ec2-user@ec2-54-154-184-132.eu-west-1.compute.amazonaws.com
```
<br>
Now that we are inside the bastion server,create a new file called "demoEC2key.pem" and paste the primary key pair we copied previously into it
<br>
Use commands below in your terminal

```bash
nano demoEC2key.pem -> This command will open the nano text editor and  help to create a file where you can paste the primary key content
press cnrtl x--> This command will close your nano file
press y + enter on your keyboard --> This command save your new changes in nano
Type chmod 400 "demoEC2key.pem" --> This command will grant permission to bastion
ssh -i "demoEC2key.pem" ec2-user@10.0.154.93 --> This command will be used to ssh into the ec2 in private subnet
```

<br>
nano demoEC2key.pem

![EC2_19](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/e913f8ab-e72e-4071-b1b2-7c1fe309dfc2)
<br>
nano demoEC2key.pem 
<br>
press cnrtl x
<br>
press y + enter on your keyboard 
<br>
Type chmod 400 "demoEC2key.pem" 
<br>
ssh -i "demoEC2key.pem" ec2-user@10.0.154.93 
<br>

![EC2_18](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/b7814662-d3a7-4df1-8b43-be411df32783)
