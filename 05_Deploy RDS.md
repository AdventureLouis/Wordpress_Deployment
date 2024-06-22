### Deploy a MariaDB RDS

![DIagram_Architecture](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/be1167c5-1c2b-46ed-b011-01573607159f)

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
Under "Engine options" choose "MariDB"

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
Under 

