# Nextcloud 22 Deployment on Ubuntu with apache server

### Run these commands to update dependencies
```
sudo apt update
```
```
sudo apt upgrade
```

### Install Unzip
```
sudo apt install unzip
```

### Install Megacmd
```
wget https://mega.nz/linux/repo/xUbuntu_20.04/amd64/megacmd-xUbuntu_20.04_amd64.deb
```
```
sudo apt install $HOME/megacmd-xUbuntu_20.04_amd64.deb
```

### Install Apache, MariaDB server and php module for apache
```
sudo apt install apache2 mariadb-server libapache2-mod-php7.4
```

### Intall some required php extensions
```
sudo apt install php7.4-gd php7.4-mysql php7.4-curl php7.4-mbstring php7.4-intl
```
```
sudo apt install php7.4-gmp php7.4-bcmath php-imagick php7.4-xml php7.4-zip
```

### Start MariaDB Server

```
service mariadb start
```

### Connect to Database

```
mariadb -u root
```

### Create Database, User and grant privileges
Create User
```
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
```
Create Databse
```
CREATE DATABASE IF NOT EXISTS nextcloud CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```
Grant Privileges
```
GRANT ALL PRIVILEGES ON nextcloud.* TO 'username'@'localhost';
```
```
FLUSH PRIVILEGES;
```
Exit form database
```
exit;
```

### Go to server directory
```
cd /var/www/html
```

### Download and unzip nextcloud package
```
wget https://download.nextcloud.com/server/releases/nextcloud-22.2.10.zip
```
```
unzip nextcloud-22.2.10.zip
```
change ownership to enable NC installation wizard
```
chown -R www-data:www-data /var/www/html/nextcloud/
```

## Apache Web server configuration
```
nano /etc/apache2/sites-available/nextcloud.conf
```
```
<VirtualHost *:80>
 DocumentRoot /var/www/html/nextcloud/
 ServerName your-server-name

  <Directory /var/www/html/nextcloud/>
    Require all granted
    AllowOverride All
    Options FollowSymLinks MultiViews

    <IfModule mod_dav.c>
      Dav off
    </IfModule>

  </Directory>
</VirtualHost>
```
Paste above code into the config file, change server name accordingly, save file and close it.

### Enable server configuration and some other modules
```
a2ensite nextcloud.conf
```
```
a2enmod rewrite headers env dir mime
```

### PHP Settings

```
nano /etc/php/7.4/apache2/php.ini
```
Change mermory limit to 512M


### Add cronjob
```
*/5  *  *  *  * php -f /var/www/nextcloud/cron.php
```

### Elasticsearch Installation
https://kenfavors.com/code/how-to-install-full-text-search-using-elastic-search-and-nextcloud/
https://najigram.com/2022/02/setup-elasticsearch-7-for-nextcloud/

