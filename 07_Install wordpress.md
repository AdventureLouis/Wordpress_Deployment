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
wget https://wordpress.org/latest.tar.gz-->This command will help install the wordpress in zip format
