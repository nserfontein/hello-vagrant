# Deploying a Complete Environment
### Install LAMP Stack
- Linux
- Apache
- MySQL
- PHP
```bash
cd ubuntu16
vagrant up
vagrant ssh

# on guest
sudo apt-get update
sudo apt-get install -y apache2 php php-mbstring php-zip phpunit unzip libapache2-mod-php

# note textual user interface for root password (TUI): use 'admin'
sudo apt-get install -y mysql-server
sudo service mysql start
mysql -u root -padmin
```

### Configure MySQL
```mysql
CREATE DATABASE myProject;
CREATE USER 'myProject'@'localhost' IDENTIFIED BY 'mypassword';
GRANT ALL PRIVILEGES ON myProject.* TO 'myProject'@'localhost';
FLUSH PRIVILEGES;
# exit
```

### Install PHP Components
```bash
# install Composer
curl -Ss http://getcomposer.org/installer | php
sudo mv composer.phar /usr/bin/composer

# change ownership of /var/www
ls -ld /var/www
sudo chown -R vagrant:vagrant /var/www
ls -ld /var/www

# install Laravel
cd /var/www
composer global require laravel/installer
```

# Deploying LAMP Stack with vagrant
### Create project
```bash
cd /var/www
composer create-project --prefer-dist laravel/laravel myProject

# confirm 
cd myProject
ls -l
```

### Change storage privileges
ls -ls storage/
chmod -R 777 storage/
ls -ls storage/

### Change serving directory
```bash
cd public
ls -l
sudo vim /etc/apache2/sites-available/000-default.conf
# DocumentRoot /var/www/myProject/public/
```

### Restart Apache
```bash
sudo apachectl restart
```

### Change MySQL settings
```bash
vim config/database.php
# 'database' => env('DB_DATABASE', 'myProject'),
# 'username' => env('DB_USERNAME', 'myProject'),
# 'password' => env('DB_PASSWORD', 'mypassword'),
```
