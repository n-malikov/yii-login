# Yii2 + Login

~~~
sudo chmod -R 777 runtime
sudo chmod -R 777 web/assets
composer install
php yii migrate
~~~

создаем админа:
~~~
http://yii-login.test/index.php?r=site/add-admin
~~~

если нужно поменять версию composer `sudo composer self-update --2`

### Apache2

создаем конфиг `yii-login.conf` на сервере

~~~
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName yii-login.test
    ServerAlias www.yii-login.test
    DocumentRoot /var/www/yii-login/web
    ErrorLog /var/www/_logs/yii-login/error.log
    CustomLog /var/www/_logs/yii-login/access.log combined
    <Directory /var/www/yii-login/web/>
        Options +FollowSymlinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
~~~

включаем

~~~
sudo a2ensite yii-login.conf
~~~

перезагружаем

~~~
sudo systemctl restart apache2
~~~