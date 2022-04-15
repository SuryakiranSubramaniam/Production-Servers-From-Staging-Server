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
~]# mysqladmin -u root -p123 flush-hosts
