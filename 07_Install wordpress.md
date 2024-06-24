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

![RDS20](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/6e6fbbe9-9b6a-4627-98de-f1df95f8bf04)


Now click "Add rule" under type choose "mysql/aurora",under protocol choose "TCP",under "port range" choose "3306",under "soure" choose "Custom" and click on search bar,scroll down until you find Bastion SG and click save
<br>

```bash
sudo systemctl start mariadb
mysql -u your user name -h your DNS endpoint -p
```
<br>
sudo systemctl start mariadb --> This command will start your mariadb
<br>
mysql -u your user name -h your DNS endpoint -p --> With this command after flag u(-u) input your master username when you created RDS in  AWS managment console,after flag h(-h) input your DNS endpoint 
<br>

![RDS21](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/7d0edb85-a475-471f-9265-f0cf5b88b164)

To get your DNS endpoint,open you AWS managment console on the search bar type RDS,click "Databases",once your database is open click on it to open your database,Under "Connectivity & security",on the left part you will see "Endpoint" that is your database endpoint name,copy it
<br>
1.e mysql -h loui-mariadb.c3oi6ac4utl8.eu-west-1.rds.amazonaws.com -u Adminloui -p
<br>
So once  you run above command,you can now view your databases,to view your databases use command
<br>
```bash
show database;
```
<br>
After running above command,you should see below 👇 
![RDS22](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/bf12c4c2-7f2e-4776-b455-acefe0b77ab0)

### Create a user for your Mariadb Database
We have been able to successfully ssh into our mariadb database now its time to create a user and password for our database with below commands
```bash
CREATE USER 'wordpress-user'@ IDENTIFIED BY 'your_strong_password';
CREATE DATABASE `wordpress-db`;
GRANT ALL PRIVILEGES ON `wordpress-db`.* TO "wordpress-user"@"localhost";
FLUSH PRIVILEGES;
```
<br>
Note that from AWS documention a variation of above command is "CREATE USER 'wordpress-user'@'localhost' IDENTIFIED BY 'your_strong_password';" but in our own command we wont include "localhost" and the reason is because our RDs is not running on our local server rather it is running on ec2 server
<br>
CREATE USER 'wordpress-user'@ IDENTIFIED BY 'your_strong_password'; --> This command will help us to create our database user and strong password
<br>
1.e CREATE USER 'loui-mariadb1'@ IDENTIFIED BY 'your_strong_password';
<br>
CREATE DATABASE `wordpress-db`; --> This command will help create your database name 1.e CREATE DATABASE `wordpress-db1`;
<br>
GRANT ALL PRIVILEGES ON `wordpress-db`.* TO "wordpress-user"; --> This command will grant all privileges of wordpress database to wordpress user 1.e GRANT ALL PRIVILEGES ON `wordpress-db1`.* TO "loui-mariadb1";
<br>

![RDS23](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/afbfd189-13d3-42e1-ab8e-7d1739b18c2e)

![RDS24](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/2a946779-2623-4d00-9d02-55678cc45308)


