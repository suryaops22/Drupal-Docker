Drupal Setup using Docker (manual)

docker pull drupal:9.5.10-php8.2-apache

mkdir -p ~/docker-drupal/{modules,profiles,sites,themes}

sudo docker run --name some-drupal --network some-network -d \
-v /home/ubuntu/docker-drupal/modules:/var/www/html/modules \
-v /home/ubuntu/docker-drupal/profiles:/var/www/html/profiles \
-v /home/ubuntu/docker-drupal/sites:/var/www/html/sites \
-v /home/ubuntu/docker-drupal/themes:/var/www/html/themes \
-p 1235:80 drupal:9.5.10-php8.2-apache

docker run -d --name some-mysql --network some-network -e MYSQL_DATABASE=drupal -e MYSQL_USER=user -e MYSQL_PASSWORD=password -e MYSQL_ROOT_PASSWORD=password mysql:5.7


docker exec -it some-mysql mysql -u user -p


Then, in your Drupal setup:

Database name: drupal
Database username: user
Database password: password
Database host: some-mysql
Database port: Leave as the default (usually 3306).


file related issues: 
mkdir -p /home/ubuntu/docker-drupal/sites/default/files
sudo chown -R www-data:www-data /home/ubuntu/docker-drupal/sites/default/files
sudo chmod -R 755 /home/ubuntu/docker-drupal/sites/default/files

settings.php issues: 
sudo chown -R www-data:www-data /home/ubuntu/docker-drupal/sites/default
sudo chmod -R 755 /home/ubuntu/docker-drupal/sites/default

copy defaulesettings.php:
docker run --name test-drupal -d -p 1234:80 drupal:9.5.10-php8.2-apache
sudo docker cp test-drupal:/var/www/html/sites/default/default.settings.php /home/ubuntu/docker-drupal/sites/default/
sudo docker cp test-drupal:/var/www/html/sites/default/default.settings.php /home/ubuntu/my-drupal-project/sites/default/settings.php
chmod 664 /path/to/your/drupal-project/sites/default/settings.php
sudo chown www-data:www-data /path/to/your/drupal-project/sites/default/settings.php
