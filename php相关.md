#### 一、编译PHP安装步骤：

1.下载php安装包：wget  http://us3.php.net/get/php-7.2.6.tar.gz 

2.解压：tar -zxvf php-7.2.6.tar.gz

3.进入解压目录

4.执行编译：

./configure --prefix=/home/homework/php --with-config-file-path=/home/homework/php/etc --enable-fpm --with-fpm-user=homework  --with-fpm-group=homework --enable-inline-optimization --disable-debug --disable-rpath --enable-shared  --enable-soap --with-libxml-dir --with-xmlrpc --with-openssl --with-mhash --with-pcre-regex --with-sqlite3 --with-zlib --enable-bcmath --with-iconv --enable-calendar --with-curl --with-cdb --enable-dom --enable-exif --enable-fileinfo --enable-filter --with-pcre-dir --enable-ftp --with-gd --with-openssl-dir --with-jpeg-dir --with-png-dir --with-zlib-dir  --with-freetype-dir --enable-gd-jis-conv --with-gettext --with-mhash --enable-json --enable-mbstring --enable-mbregex --enable-mbregex-backtrack --with-libmbfl --with-onig --enable-pdo --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-zlib-dir --with-pdo-sqlite --enable-session --enable-shmop --enable-simplexml --enable-sockets  --enable-sysvmsg --enable-sysvsem --enable-sysvshm --enable-wddx --with-libxml-dir --with-xsl --enable-zip --enable-mysqlnd-compression-support --with-pear --enable-opcache

5. make && make install
6. 拷贝源码包中的php.ini.production or php.ini.developmet配置文件到php安装目录的etc文件夹下
7. 更改相关配置：日志文件配置、php-fpm配置（php-fpm.d/www.conf.default）
8. 把php添加到系统路径中：export PATH=$PATH:/home/homework/php/sbin
9. php -v即可查看到安装完毕

#### 二、编译安装PHP相关拓展

1、memcached、memcache、redis、msgpack等

2、涉及相关命令：

/home/homework/php/bin/phpize 

./cofigure —with-php-config=/home/homework/php/bin/php-config

make 

make install

3、编辑php.ini文件，添加拓展extension=xx.so，重启php-fpm和nginx服务即可。

4、查看扩展是否安装OK：php -m | grep xxx

5、查看php配置文件位置：php -i | grep ini 

遇到问题参考：

https://stackoverflow.com/questions/37550910/memcache-extension-with-php-7-on-centos-fails-to-install



