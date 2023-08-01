This Repo has the default Drupal Application.

The main reason to create this repo is to store the docker-compose.yml file, the repo doesn't have any real application.

The docker-compose.yml file contains
> Install drupal using docker - drupal version - drupal:9.5.10-php8.2-apache
> Install MYSQL using docker  - MYSQL version  - mysql:5.7
> creating the communication between the two containers using the same network - network used - some-network
> creating the bind-mouts using '-v' flag in docker-compose file

Here, the configurations used for MYSQL are:

Database name: drupal
Database username: user
Database password: password
Database host: mysql (the name of the MySQL service in the docker-compose file)

