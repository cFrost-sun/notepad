## 新建用户

```
CREATE USER 'xxxx'@'localhost' IDENTIFIED BY 'xxxxx';
```

## 删除用户

```
DROP USER xxxx;
DROP USER 'xxxx'@'localhost';
```

## 用户赋权

```
GRANT ALL PRIVILEGES ON *.* TO 'user'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;
```

## 刷新权限

```
FLUSH PRIVILEGES;
```

## 克隆数据库

```
mysqldump -u root -p lhen > lhen-release.sql
mysql -u 用户名 -p --database 数据库名 < D:abc.sql
```

MySql
授权：
SET PASSWORD = PASSWORD('some password') SET PASSWORD FOR user = PASSWORD('some password')
grant all on *.* to 'root'@'localhost' IDENTIFIED BY '你的密码'with grant option ;
flush privileges;
update user set password=password('你的密码') where user='root';
查看编码
show variables like 'char%';
查看数据文件位置
show variables like '%dir%';
vi /etc/rc.d/init.d/mysql

克隆数据库
mysqldump -u root -p lhen > lhen-release.sql
mysql -u 用户名 -p --database 数据库名 < D:abc.sql


#给用户cacti赋予所有库的所有权限  
GRANT ALL PRIVILEGES ON *.* TO 'cacti'@'%' IDENTIFIED BY 'cacti' WITH GRANT OPTION;  
#重新载入赋权表  
FLUSH PRIVILEGES;  
  
#收回权限(不包含赋权权限)  
REVOKE ALL PRIVILEGES ON *.* FROM cacti;  
REVOKE ALL PRIVILEGES ON cacti.* FROM cacti;  
##收回赋权权限  
REVOKE GRANT OPTION ON *.* FROM cacti;  
##重新载入赋权表  
FLUSH PRIVILEGES; 


docker run --name mysql -p 63001:3306 -v $DOCKER_RUNTIME/mysql/data:/var/lib/mysql -v $DOCKER_RUNTIME/mysql/conf:/etc/mysql/conf.d -d mysql:5.6.35

docker run -d -p 49001:8080 --add-host repo.eulerproject.io:10.116.122.40 --privileged=true --name jenkins -v $DOCKER_RUNTIME/jenkins:/var/jenkins_home:rw -t cfrost/my-jenkins:0.0.1

grant all on *.* to 'root'@'localhost' IDENTIFIED BY 'aXucYe.Ja163#' with grant option;
REVOKE ALL PRIVILEGES ON *.* FROM 'root'@'%';
REVOKE GRANT OPTION ON *.* FROM 'root'@'%';
create database euler_framework_demo;
grant all on euler_framework_demo.* to 'root'@'%' IDENTIFIED BY 'aXucYe.Ja163#' with grant option;
FLUSH PRIVILEGES;

