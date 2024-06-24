### Install Wordpress

![DIagram_Architecture](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/cc8f3287-bb38-48dc-ab58-fca8dcb7c660)
<br>
Now its time to install the wordpress
<br>
so recall we need first need to ssh into the bastion and from the bastion ssh into the ec2 in private instance
<br>
Type below commands

```bash
wget https://wordpress.org/latest.tar.gz
tar -xzf latest.tar.gz
sudo systemctl start mariadb
```
![install_wp1](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/56d62e5e-5d14-40d5-9a33-b029b4344f94)
<br>
wget https://wordpress.org/latest.tar.gz-->This command will help install the wordpress in zip format using tar .gz
<br>
tar -xzf latest.tar.gz --> This command will unzip and extract the installation files into a folder called  the wordpress 
<br>

#### Create a database user and database for the wordpress
<br>
Before running below commands,we first need to grant security group access to the mariadb RDS
<br>

![RDS13](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/3e386efd-b4cf-4e5a-957c-db6fa806ddc4)

To achieve this open you AWS managment console on the search bar type RDS,click "Databases",once your database is open click on it to open your database as shown above
<br>

![RDS14](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/9c660ee8-ca4c-4804-996e-32afa36c807b)

Under "Connectivity & security",click on the security group on the right corner to open your security group as seen above
<br>

![RDS15](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/62ae4608-ed95-408c-a6b3-2341378b56a7)

Once your security group is open,check the box next to it so that that tabs below can be displayed as seen above
<br>

![RDS16](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/ffefc559-e9aa-4cbc-85c8-c4915ee9c328)

Next click "Inbound rules" and "Edit inbound rules" as we can see from above this security group is pointing to our IP but we want this security group to have same SG as the ec2 server and  bastion server because  we want our RDS to be in the ec2 server
<br>

![Screenshot 2024-06-24 at 4 11 28 PM](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/baf935c9-1443-446e-a22b-362a22013ff7)
Now we are in Edit page of the resource group,click delete on the right corner to delete the resource group
<br>

![RDS18](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/9c93c08b-da75-4a0d-b2a9-4e2fcc6c3b8f)

![RDS19](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/2d44a72c-054f-49b6-a962-3666f0c3ebf1)

Now click "Add rule" under type choose "mysql/aurora",under protocol choose "TCP",under "port range" choose "3306",under "soure" choose "Custom" and click on search bar,scroll down until you find Bastion SG and click save




```bash
sudo systemctl start mariadb
mysql -u your user name -h your DNS endpoint -p
```
