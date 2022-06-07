# Yii2 + RBAC

~~~
sudo chmod -R 777 runtime
sudo chmod -R 777 web/assets
composer install
php yii migrate
~~~

если нужно поменять версию composer

~~~
sudo composer self-update --2
~~~

### Apache2

создаем конфиг `y-rbac.conf` на сервере

~~~
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName y-rbac.test
    ServerAlias www.y-rbac.test
    DocumentRoot /var/www/y-rbac/web
    ErrorLog /var/www/_logs/y-rbac/error.log
    CustomLog /var/www/_logs/y-rbac/access.log combined
    <Directory /var/www/y-rbac/web/>
        Options +FollowSymlinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
~~~

включаем

~~~
sudo a2ensite y-rbac.conf
~~~

перезагружаем

~~~
sudo systemctl restart apache2
~~~