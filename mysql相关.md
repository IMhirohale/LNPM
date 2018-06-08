具体步骤和一般软件编译安装一致，这里简单记录本人遇到的问题。

```
wget http://cdn.mysql.com/Downloads/MySQL-5.6/mysql-5.6.14.tar.gz
tar xvf mysql-5.6.14.tar.gz
cd mysql-5.6.14

cmake -DCMAKE_INSTALL_PREFIX=/root/mysql -DMYSQL_DATADIR=/root/mysql/data -DSYSCONFDIR=/root/mysql/etc -DWITH_INNOBASE_STORAGE_ENGINE=1 -DWITH_PARTITION_STORAGE_ENGINE=1 -DWITH_FEDERATED_STORAGE_ENGINE=1 -DWITH_BLACKHOLE_STORAGE_ENGINE=1 -DWITH_MYISAM_STORAGE_ENGINE=1 -DENABLED_LOCAL_INFILE=1 -DENABLE_DTRACE=0 -DDEFAULT_CHARSET=utf8mb4 -DDEFAULT_COLLATION=utf8mb4_general_ci -DWITH_EMBEDDED_SERVER=1

groupadd -r mysql && useradd -r -g mysql -s /sbin/nologin -M mysql 

初始化数据库很重要，否则启动不起来
scripts/mysql_install_db --basedir=/root/mysql --datadir=/root/mysql/data --user=mysql

添加服务，拷贝服务脚本到init.d目录，并设置开机启动
cp support-files/mysql.server /etc/init.d/mysqld
chkconfig mysqld on
service mysqld start  --启动MySQL

添加mysql到系统变量
export PATH=$PATH:/home/homework/mysql/bin

设置用户登录密码
/root/mysql/bin/mysqladmin -u root password 'new-password'

授权支持远程访问
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'passwd' WITH GRANT OPTION;
```





参考：

https://www.cnblogs.com/xiongpq/p/3384681.html

https://www.jianshu.com/p/95a103add722

