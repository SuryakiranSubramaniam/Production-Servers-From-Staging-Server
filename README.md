# Production-Servers-From-Staging-Server
Production-Servers-From-Staging-Server

![alt text](https://github.com/SuryakiranSubramaniam/Production-Servers-From-Staging-Server/blob/main/image/Production.png)

## Create a Classic Internal Load Balancer

Dont forgot to check ***Create an internal load balancer:***
![alt text](https://github.com/SuryakiranSubramaniam/Production-Servers-From-Staging-Server/blob/main/image/ICLB1.png)

![alt text](https://github.com/SuryakiranSubramaniam/Production-Servers-From-Staging-Server/blob/main/image/ICLB2.png)

![alt text](https://github.com/SuryakiranSubramaniam/Production-Servers-From-Staging-Server/blob/main/image/ICLB.png)

![alt text](https://github.com/SuryakiranSubramaniam/Production-Servers-From-Staging-Server/blob/main/image/ICLB3.png)

![alt text](https://github.com/SuryakiranSubramaniam/Production-Servers-From-Staging-Server/blob/main/image/ICLB4.png)

![alt text](https://github.com/SuryakiranSubramaniam/Production-Servers-From-Staging-Server/blob/main/image/ICLB5.png)

## Now test the Classic Internal Load Balancer

## Loag into an instance in your aws account:

 ~]# mysql -u project -pdbuserpass -h internal-master2master-609233073.ap-south-1.elb.amazonaws.com -e 'select * from company.employees;'
 
 +------+-------+
| ID   | Name  |
+------+-------+
|    1 | surya |
+------+-------+

#### (Warning Dont use unnecessary) Can be used in case of any error:

Login to any DB server : 

~]# mysqladmin -u root -p123 flush-hosts

## Now LogIn to the Staging server

vim /var/www/html/wp-config.php

/** Database hostname */
define( 'DB_HOST', 'internal-master2master-609233073.ap-south-1.elb.amazonaws.com' );

## Login to any DB server : 

~]# scp -r root@172.31.39.170:/root/wordpress.sql .

~]# mysql -u root -p123

MariaDB [(none)]> create database wordpress;

~]# mysql -u root -p123 wordpress < wordpress.sql

~]# mysql -u root -p123

MariaDB [(none)]> use wordpress;

MariaDB [wordpress]> UPDATE wp_options SET option_value = replace(option_value, 'dev.suryakiran.online', 'prod.suryakiran.online') WHERE option_name = 'home' OR option_name = 'siteurl';UPDATE wp_posts SET guid = replace(guid, 'dev.suryakiran.online','prod.suryakiran.online');UPDATE wp_posts SET post_content = replace(post_content, 'dev.suryakiran.online', 'prod.suryakiran.online'); UPDATE wp_postmeta SET meta_value = replace(meta_value,'dev.suryakiran.online','prod.suryakiran.online');

## Now create an AMI from staging server

## Create a Target Group

## Create a Launch configurations

## Create an Auto Scaling groups

## Now the Instancess will be created under the target group we created

## Now set up the ALB

From Listener click View/edit rules

## Now Add Rout 53 Records

