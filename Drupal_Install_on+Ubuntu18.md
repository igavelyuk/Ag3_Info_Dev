# Drupal install on Ubuntu

## Overview
So in this lesson we will install Drupal on Apache2  on the Ubuntu.

## Install LAMP
```bash
sudo apt install apache2 vsftpd mysql-server mysql-client php7.2 libapache2-mod-php7.2 php7.2-mysql php7.2-curl php7.2-json php-gd php-bcmath;/etc/init.d/apache2 restart

```

## Install Dev env
```bash
add-apt-repository ppa:webupd8team/atom
sudo apt update; sudo apt install atom
sudo apt install git phpmyadmin nodejs npm composer
```
## Configure apache2

cd /etc/apache2
cp apache2.conf apache2.bak
cd ../
cd ../
sudo nano /etc/apache2/sites-available/000-default.conf

```bash
<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        ServerName drupal.site
        ServerAlias www.drupal.site
        DocumentRoot /var/www/drupal.site

        <Directory /var/www/drupal.site>
        AllowOverride All
         RewriteEngine On
         RewriteBase /
         RewriteCond %{REQUEST_FILENAME} !-f
         RewriteCond %{REQUEST_FILENAME} !-d
         RewriteRule ^(.*)$ index.php?q=$1 [L,QSA]
         </Directory>

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

```
## MySQL and phpMyAdmin (https://askubuntu.com/questions/763336/cannot-enter-phpmyadmin-as-root-mysql-5-7)
1. Connect to mysql

`sudo mysql --user=root mysql`

2. Create a user for phpMyAdmin

Run the following commands (replacing some_pass by the desired password):

```mysql
CREATE USER 'phpmyadmin'@'localhost' IDENTIFIED BY 'some_pass';
GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```
If your phpMyAdmin is connecting to localhost, this should be enough.
3. Optional and unsafe: allow remote connections

Remember: allow a remote user to have all privileges is a security concern and this is not required in most of cases.

With this in mind, if you want this user to have the same privileges during remote connections, additionally run (replacing some_pass by the password used in Step #2):

CREATE USER 'phpmyadmin'@'%' IDENTIFIED BY 'some_pass';
GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;

4. Update phpMyAdmin

Using sudo, edit /etc/dbconfig-common/phpmyadmin.conf file updating user/password values in the following sections (replacing some_pass by the password used in Step #2):
```
# dbc_dbuser: database user
#       the name of the user who we will use to connect to the database.
dbc_dbuser='phpmyadmin'

# dbc_dbpass: database user password
#       the password to use with the above username when connecting
#       to a database, if one is required
dbc_dbpass='some_pass'

```
