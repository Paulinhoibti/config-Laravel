### GUIA DE INSTALAÇÃO E COMANDOS DO DOCKER 2020.2

## Instalação do Docker 


curl -sSL http://get.docker.com | sh
docker run -it --name APLICAÇÂO -v ~/projects/:/var/www/ -p 80:80 debian
sudo apt-get install -y php5
sudo apt-get install -y apache2
sudo apt install mysql


## Instalação do Composer no Projeto ##


curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer



## Criação do projeto ##

composer create-project --prefer-dist laravel/laravel blog


## configuração do projeto 

sudo chgrp -R www-data /var/www/html/blog
sudo chmod -R 775 /var/www/html/blog/storage


## *** Configuração do Apache  ***

cd /etc/apache2/sites-available
sudo nano laravel.conf

 <VirtualHost *:80>
     ServerName zf2-tutorial.localhost
     DocumentRoot /path/to/zf2-tutorial/public
     <Directory /path/to/zf2-tutorial/public>
         DirectoryIndex index.php
         AllowOverride All
         Order allow,deny
         Allow from all
     </Directory>
 </VirtualHost>

sudo a2dissite 000-default.conf
sudo a2ensite laravel.conf
sudo a2enmod rewrite
sudo service apache2 restart



## Caso ocorra algum problema
php artisan cache:clear 
chmod -R 777 app/storage 
composer dump-autoload


## ***
