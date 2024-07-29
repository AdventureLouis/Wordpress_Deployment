### Deploy a MariaDB RDS

![System_Architecture_By_Louis](https://github.com/user-attachments/assets/bfd16425-d360-4ee3-b51c-ce498ecfddc1)


<br>
The RDS we will be deploying in the session is Mariadb and the reason is because MariadDB is widely used and when compared to Mysql Mariadb is slightly faster
<br>

![RDS1](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/a6eab676-5d14-44c3-955b-ca6d80e1e097)

Open your AWS management console and on the search bar type RDS as shown above and click to open the RDS page
<br>
Once its open on the left pane click "Databases"

![Screenshot 2024-06-22 at 5 09 41 PM](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/769b51d6-b017-4307-ad73-c9128027c9d9)
<br>
Under "create Database" choose "Standard create"
<br>
Under "Engine options" choose "MariaDB"

![RDS3](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/c8e0ecfd-0e42-4ce1-a1be-1300631f243d)

<br>
Under "show filters",leave it at default and dont toggle "how versions that support the Amazon RDS Optimized Writes"
<br>
Under "Engine version" leave at latest version
Under "Templates" choose "Free Tier"
<br>
Under "DB instance identifier" give a name to it
<br>
Under "Credential Settings" give a "master username"
<br>

![RDS4](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/e4ef53c2-08bf-46f7-a406-ffedefd75ed5)
<br>
Under "Credentials management" set to "Self managed"
<br>
Under  "Master Password" set your password
<br>
Under "Instance configuration" choose "db.t3.micro"
<br>

![RDS5](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/00a974b4-bd26-4504-87a6-def1d9c71c4d)
<br>
Under "Storage",leave at "General Purpose SSD" (gp2)
<br>
Under "Allocated storage" set it to 20GB
<br>
Under "Storage autoscaling" enable sutoscaling
<br>

![RDS6](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/47f41331-b34a-4a30-82d6-33dbf0074135)
<br>
Under "Availability & durability" because we are using free tier we cannot use it
<br>
Under "Compute resource" check the box next to "Don’t connect to an EC2 compute resource" because we want to connect manually
<br>
Under "Network type" choose "IPV4"
<br>
Under "Virtual private cloud (VPC)" choose the VPC that we previously created
<br>

![RDS7](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/1cffbf19-6024-4aff-a743-68ad36ccde92)
<br>
Under "DB subnet group" choose "create new subnet group"
<br>
Under "public access" choose No
<br>
Under "VPC security group (firewall)" create a new security group for the Database and give it a name
<br>
Under  "Availability Zone" choose Availabilty zone of your choice
<br>
Under "RDS Proxy" uncheck the box to avoid additional cose
<br>
Under "Certificate authority - optional" leave default
<br>

![RDS8](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/3c2656b1-47b0-4dae-a9ac-b76c9e7f8b2e)

<br>
 
Under "Additional configuration" we can see that the database port is set to 3606,leave as default
<br>
Under "Database authentication" set to "Password authentication"
<br>
Under "Monitoring" uncheck the the box
<br>

![RDS9](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/4423fd56-16e0-4796-b580-e41e58323a22)
<br>
Under "Additional Configuration" again click on the drop-down to see more options
<br>
Under "Initial Database Name" choose your Database name
<br>
Under "DB parameter group" leave it at default
<br>
Under "Backup" check the box to enable backup
<br>
Under "Backup window" leave it at default
<br>
Under "Backup replication" Uncheck the box
<br>
Under Encryption,check the box to enable encryption and for the encryption leave it at default
<br>

![RDS10](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/746bc440-068b-4bb2-9024-a21ac4ece727)
<br>

Under "Maintenance" check the box to "Enable auto minor version upgrade"
<br>
Under "Maintenance window" choose no preference
<br>
Under "Deletion protection" check the box and click create database

![RDS11](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/41bb8838-9918-4086-9c0b-a3aaf3c91a0f)

![RDS12](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/28cb109b-50f5-4dd6-9c3f-3b8829502497)

