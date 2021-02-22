# nextcloud
# when you try to install nextcloud you will have face 3 main issue.
# 1 PHP 7.0 or above
# 2 Mariadb version 10 or higher
# 3 web server
# first we are instatinlg  PHP and some more pacakges 
amazon-linux-extras enable php7.4
yum -y install vim httpd php php-cli php-mysqlnd php-zip php-devel php-gd php-mcrypt php-mbstring php-curl php-xml php-pear php-bcmath php-json php-pdo php-pecl-apcu php-pecl-apcu-devel
# for just check php version.
php -v
# now we are installting mariadb version 10
cat > /etc/yum.repos.d/mariadb.repo
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.3/centos7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
ctrl + d
yum install mariadb mariadb-server
systemctl start mysql
systemctl enable mysql
# now we are configure mariadb server
mysql_secure_installation
after the installtion
create user 'give_username'@'localhost' identified by 'type_password';
create database (databasename);
grant all privileges on databasename.* to 'username'@'localhost' identified by 'password';
flush privileges;
exit
now download the nextcloud application
wget https://download.nextcloud.com/server/releases/latest-20.zip
unzip latest-20.zip 
yum install httpd -y
systemctl start httpd
systemctl enable httpd
mv nextcloud/* /var/www/html/
mkdir /var/www/html/data
chown apache:apache -R /var/www/html














