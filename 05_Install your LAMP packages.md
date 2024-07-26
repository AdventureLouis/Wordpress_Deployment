### Update EC2 and install your LAMP packages

![System_Achitecture](https://github.com/user-attachments/assets/71796aa4-a3fb-4b1b-8044-7a63766b44f9)


<br>
Now you need to ssh in your ec2 instance,update the ec2 to latest version and install LAMP(Linux,Apache,Mysql,PHP) services.In order to be able to successfully install the wordpress we need all these services.
<br>

#### Install Apache http webserver,Mariadb10.5 and PHP8.2
After you ssh into your ec2 through your bastion server,run below commands

``` bash
sudo yum update -y
sudo amazon-linux-extras install mariadb10.5
cat /etc/system-release
sudo amazon-linux-extras install php8.2
sudo yum install -y httpd
yum info package_name
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl is-enabled httpd

```
sudo yum update -y --> This command will update your ec2 instance to latest version and the flag y (-y) will help to automatically keep responding "yes" when promoted to respond
<br>
sudo amazon-linux-extras install mariadb10.5 --> This command will help to install the mariadb version 10.5
<br>
cat /etc/system-release --> This will help to show your version of amazon linus installed
<br>
sudo amazon-linux-extras install php8.2 --> This command will help to install php8.2
<br>
sudo yum install -y httpd --> This command will help to install the http webserver and the flag y(-y) will help to automatically keep responding "yes" to prompts that needs response
<br>
yum info package_name --> With this command you can get info of the current version of services that you have installed 1.e yum info httpd
<br>
sudo systemctl start httpd --> With this command you start the http webserver
<br>
sudo systemctl enable httpd --> This command can help to initiate the http webserver whenever it is rebooted,because sometimes the services might be started but it is not enabled and as such the service wont work
<br>
sudo systemctl is-enabled httpd --> This command will help to check to see if the http webserver is enabled

#### Set file permissions to 
<br>

```bash
sudo usermod -a -G apache ec2-user
exit
sudo chown -R ec2-user:apache /var/www
groups
sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;
find /var/www -type f -exec sudo chmod 0664 {} \;
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php
sudo yum list installed httpd mariadb-server php-mysqlnd
rm /var/www/html/phpinfo.php
```
<br>

sudo usermod -a -G apache ec2-user --> With this commands you have the root user(sudo) super priviledges,"usermod" will help to modify the ec2 user, flag a (-a) will help to append the ec2-user to the group without removing it from any group they previously belong to,flag apache G(-G) will help to attach the ec2-user to the apache group.
<br>
exit --> This command will help you to exit from the ec2 so that changes can be effected and login to verify that the ec2-user now belong to the Apache group
<br>
groups --> This command will help to verify if the ec2-user now belong to the Apache group
<br>
sudo chown -R ec2-user:apache /var/www --> With this command "chown" will help to change ownership of the Apache document directory(/var/www)
to the Apache group which the ec2-user now belongs to (ec2-user:apache) and the flag R(-R) will help to implement this recursively for the contents of the Apache document directory.
<br>
sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \; --> This command sets the directory permissions of the root directory /var/www to 2775. The 2 at the begining ensures that the new files and directories inherit the group ownership and the 775 permissions grant read,write, and execute permissions to the owner and group
<br>
find /var/www -type f -exec sudo chmod 0664 {} \; -->The command set the permissions of /var/www and its subdirectories to 0664.The
6 at the begining grants read and write permissions to the owner and group and grants read permissions to others.
<br>
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php --> This command will create a php file in the Apache document root
<br>
sudo yum list installed httpd mariadb-server php-mysqlnd --> This command will install the mariadb server and the php
<br>
rm /var/www/html/phpinfo.php -->This command will delete the file phpinfo.php





