### Install Wordpress



![System_Architecture_By_Louis](https://github.com/user-attachments/assets/48fb06a6-3669-4b6b-995c-aca8637b034d)

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
show database;
exit
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

After running all commands above,type "show databses" to show your database
<br>
And finally type exit to exit from mysql client
<br>

![RDS23](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/afbfd189-13d3-42e1-ab8e-7d1739b18c2e)

![RDS24](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/2a946779-2623-4d00-9d02-55678cc45308)
<br>

 ### Create and edit wp-config.php file
The wp-config.php is a wordpress confgiguration file,now we want to edit this file but we dont want the edit to be implemented on the original file so we create a new file called wp-config-sample.php which will serve as a backup file and edit the original file,use commands below
<br>
```bash
cp wordpress/wp-config-sample.php wordpress/wp-config.php
nano wordpress/wp-config.php
```
<br>
cp wordpress/wp-config-sample.php wordpress/wp-config.php --> With this command a new file called wp-config-sample.php will be created and all contents from wp-config.php will be copied into the new file
<br>
nano wordpress/wp-config.php --> This command will open  wp-config.php file in nano text editor as seen below 👇 

![RDS25](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/06b81e19-3aa6-4fc0-b823-73300429a4f9)

<br>

Once the text editor is open,keep scrolling down until you get to a place we you see "define('DB_NAME', 'wordpress-db');" and replace with your database name
<br>
Next scroll down to where you have "define('DB_USER', 'wordpress-user');" and replace with your database username
<br>
Next scroll down to where you have define('DB_PASSWORD', 'your_strong_password'); and replace with your strong password
<br> 
Next scroll down until you see below :
define('AUTH_KEY',         ' #U$$+[RXN8:b^-L 0(WU_+ c+WFkI~c]o]-bHw+)/Aj[wTwSiZ<Qb[mghEXcRh-');
define('SECURE_AUTH_KEY',  'Zsz._P=l/|y.Lq)XjlkwS1y5NJ76E6EJ.AV0pCKZZB,*~*r ?6OP$eJT@;+(ndLg');
define('LOGGED_IN_KEY',    'ju}qwre3V*+8f_zOWf?{LlGsQ]Ye@2Jh^,8x>)Y |;(^[Iw]Pi+LG#A4R?7N`YB3');
define('NONCE_KEY',        'P(g62HeZxEes|LnI^i=H,[XwK9I&[2s|:?0N}VJM%?;v2v]v+;+^9eXUahg@::Cj');
define('AUTH_SALT',        'C$DpB4Hj[JK:?{ql`sRVa:{:7yShy(9A@5wg+`JJVb1fk%_-Bx*M4(qc[Qg%JT!h');
define('SECURE_AUTH_SALT', 'd!uRu#}+q#{f$Z?Z9uFPG.${+S{n~1M&%@~gL>U>NV<zpD-@2-Es7Q1O-bp28EKv');
define('LOGGED_IN_SALT',   ';j{00P*owZf)kVD+FVLn-~ >.|Y%Ug4#I^*LVd9QeZ^&XmK|e(76miC+&W&+^0P/');
define('NONCE_SALT',       '-97r*V/cgxLmp?Zy4zUU4r99QQ_rGs2LTd%P;|_e1tS)8_B/,.6[=UK<J_y9?JWG');
<br>
You will need to replace above because they can be generated randomly,use link below
<br>
```bash
https://api.wordpress.org/secret-key/1.1/salt/
```
In order to paste in your nano text editor first remove above with command cntrl+k until remove all then paste the new ones you copied from above site.close and save your nano text editor with commands

```bash
cntr+x,y,enter on your keyboard
```
<br>

#### Install wordpress file under the Apache document directory
<br>
Recall that in session 06,we already attached the ec2-user to Apache document directory group(/var/www/),now we want to attach our wordpress that is inside our ec2 instance to Apache document directory(/var/www/html)

```bash
cp -r wordpress/* /var/www/html/
sudo nano /etc/httpd/conf/httpd.conf
```
![RDS27](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/dabc43d3-7db6-4b56-af81-9f56cf620299)

<br>
cp -r wordpress/* /var/www/html/ --> The command will recursively(-r) copy all installation files from the wordpress folder into the Apache root directory
<br>
sudo nano /etc/httpd/conf/httpd.conf --> This command will the httpd configuration file in nano text editor
<br>
Once  httpd configuration file(httpd.conf) is open use command cntrl+w to open a search bar on nano and once the search bar is open paste

 ```  <Directory "/var/www/html"> ```  to find it and change "AllowOverride None" to "AllowOverride All" then save
<br>
 
![RDS28](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/ca1ceb5f-ff87-4a55-92b0-f1cf01b86962)

#### Install php graphics drawing library
<br>

``` bash
sudo yum install php-gd
sudo yum list installed php-gd
```
<br>
sudo yum install php-gd --> This command utilizes the root super privilege to install php graphics drawing library
<br>
sudo yum list installed php-gd -->This command verify the installed version of php graphics drawing library

![RDS29](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/88947dbb-0b7c-49e8-89b1-943b507c08e9)

#### File permissions to Apache Webserver
<br>

```bash
sudo chown -R apache /var/www
sudo chgrp -R apache /var/www
sudo chmod 2775 /var/www
find /var/www -type d -exec sudo chmod 2775 {} \;
find /var/www -type f -exec sudo chmod 0644 {} \;
sudo systemctl restart httpd
```
<br>
sudo chown -R apache /var/www -->This command will recursively copy wordpress files that is currently in apache root directory into apache web server
<br>
sudo chgrp -R apache /var/www -->

