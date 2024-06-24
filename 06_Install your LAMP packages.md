### Update EC2 and install your LAMP packages

![DIagram_Architecture](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/fc01464b-1570-4cc3-b129-d07a16117133)
<br>
Now you need to ssh in your ec2 instance,update the ec2 to latest version and install LAMP(Linux,Apache,Mysql,PHP) services.In order to be able to successfully install the wordpress we need all these services.
<br>

#### Install Apache http webserver
After you ssh into your ec2 through your bastion server,run below commands

``` bash
sudo yum update -y
sudo amazon-linux-extras install mariadb10.5
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
sudo yum install -y httpd --> This command will help to install the http webserver and the flag y(-y) will help to automatically keep responding "yes" to prompts that needs response
<br>
yum info package_name --> With this command you can get info of the current version of services that you have installed 1.e yum info httpd
<br>
sudo systemctl start httpd --> With this command you start the http webserver
<br>
sudo systemctl enable httpd --> This command can help to initiate the http webserver whenever it is rebooted,because sometimes the services might be started but it is not enabled and as such the service wont work
<br>
sudo systemctl is-enabled httpd --> This command will help to check to see if the http webserver is enabled

### Set file permissions
<br>

```bash
sudo usermod -a -G apache ec2-user
exit
sudo chown -R ec2-user:apache /var/www
sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;
find /var/www -type f -exec sudo chmod 0664 {} \;
sudo yum list installed httpd mariadb-server php-mysqlnd
rm /var/www/html/phpinfo.php
```


