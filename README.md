## LinuxMint WebServer HOW TO

### LinuxMint 18.2 instructions for install web server for Drupal8

#### 1.Project
 * Project created as instruction set
#### 2. Description how to proper install
 * Create superuser:
  ```
  sudo passwd root
  ENTER PASSWORD
  ```
 * Login as superuser
  ```
  su
  ENTER PASSWORD
  ```

 * Install Apache 2 and FTP: `apt install apache2 vsftpd`

 * Install MySQL:`apt install mysql-server mysql-client`

 * Install PHP7:`apt install php7.0 libapache2-mod-php7.0 php7.0-mysql php7.0-curl php7.0-json php-gd php-bcmath`
 * Restart apache2 `/etc/init.d/apache2 restart
`
 * Check php working
  ```bash
  cd /var
  chmod 777 www -R
  cd /var/www/html/
  mv index.html index.2.html
  nano info.php

  ```

   * write text in nano `<?php phpinfo(); ?>`

 * Clear URL for Drupal:
   * `nano /etc/apache2/sites-available/000-default.conf`
   * If inside you have `<Directory "/var/www">` section find `AllowOverride None` change to `AllowOverride All`

* Install Development Environment:
  ```
  apt install phpmyadmin
  add-apt-repository ppa:webupd8team/atom
  apt update; apt install atom
  apt install git
  apt install nodejs
  apt install npm
  apt install composer
  ```
* Install Last Updates for Drupal8:
* Change privileges of /usw/www to webserver
 ```bash
  su
  [PASSWORD]
  chown www-data:www-data www -R
  chmod 777 www -R
  curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
  ```
* or
  ```bash
  curl -sS https://getcomposer.org/installer | php
  ```
* then
 ```bash
 php composer.phar install
 cd /var/www/html/
 composer config repositories.drupal composer https://packages.drupal.org/8
 composer require "drupal/address ~1.0"
 composer update drupal/address --with-dependencies
 ```
#### Quick copy paste
 Install all and after restart server
 ```
 apt install apache2 vsftpd mysql-server mysql-client php7.0 libapache2-mod-php7.0 php7.0-mysql php7.0-curl php7.0-json php-gd php-bcmath;/etc/init.d/apache2 restart
 ```
 * Change `/etc/apache2/apache2.conf`
 ```
  <Directory "/var/www">
        Options Indexes FollowSymLinks
        AllowOverride All
  </Directory>
 ```
 * Add .htacess to Drupal folder /var/www
 ```JavaScript
 RewriteEngine on
 RewriteBase /
 RewriteCond %{REQUEST_FILENAME} !-f
 RewriteCond %{REQUEST_FILENAME} !-d
 RewriteCond %{REQUEST_URI} !=/favicon.ico
 RewriteRule ^ index.php [L]
 ```

#### Phpmyadmin deprecation error solver
 ```
 apt-get remove --purge phpmyadmin php-gettext php-mbstring -y
 apt-get autoremove -y
 apt-get update
 apt-get install phpmyadmin php-gettext php-mbstring -y
 ```

  Version: `0.6a`
  Date: `23.10.2017`
