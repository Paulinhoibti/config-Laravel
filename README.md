# config-Laravel
---
——- Instalação do Docker ———-
curl -sSL http://get.docker.com | sh
docker run -it --name APLICAÇÂO -v ~/projects/:/var/www/ -p 80:80 debian
sudo apt-get install -y php5
sudo apt-get install -y apache2
---
——- configuração do Apache ———-

cd /etc/apache2/sites-available
sudo nano laravel.conf

<VirtualHost *:80>
    ServerName localhost

    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html

    <Directory /var/www/html/>
        AllowOverride All
    </Directory>
</VirtualHost>


——- Instalação do Composer ———-

php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '55d6ead61b29c7bdee5cccfb50076874187bd9f21f65d8991d46ec5cc90518f447387fb9f76ebae1fbbacf329e583e30') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php --install-dir=/bin --filename=composer

curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer


——- Criação do projeto ———-

composer create-project --prefer-dist laravel/laravel blog


——- configuração do projeto ———-

sudo chgrp -R www-data /var/www/html/blog
sudo chmod -R 775 /var/www/html/blog/storage



sudo a2dissite 000-default.conf
sudo a2ensite laravel.conf
sudo a2enmod rewrite
sudo service apache2 restart


——- Caso ocorra algum problema ———-

Error in exception handler

php artisan cache:clear 
chmod -R 777 app/storage 
composer dump-autoload



