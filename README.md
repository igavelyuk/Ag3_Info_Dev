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
 * Check php working
  ```
  cd /var
  chmod 777 www -R

  cd /var/www/html/
  mv index.html index.2.html
  nano info.php
  ```
   * write text in nano `<?php phpinfo(); ?>`

 * Clear URL for Drupal:
   * `nano /etc/apache2/sites-available/000-default.conf`
   * change DirectoryRoot /var/www/html to DirectoryRoot /var/www and paste Directory section

  ```
  DirectoryRoot /var/www

  <Directory /var/www/html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
  </Directory>
  ```

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
  ```
  su
  [PASSWORD]
  curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
  ```
* or
  ```
  curl -sS https://getcomposer.org/installer | php
  ```
* then
 ```
 php composer.phar install
 cd /var/www/html/

 composer config repositories.drupal composer https://packages.drupal.org/8
 composer require "drupal/address ~1.0"
 composer update drupal/address --with-dependencies
 ```
  Version: `0.5a`
  Date: `22.10.2017`
