# Wordpress theme

## Prerequisites:

Docker and docker-compose.

## Steps

Starting here: [How to Convert HTML Website into WordPress Business Theme](https://www.cloudways.com/blog/html-to-wordpress/)\
YAML file to start with docker-compose. Replace name-of-the-theme with the name of your theme and create a folder in your current folder with the same name, this is to have the ability to store your theme on Github. You should replace the variables of your database and Wordpress installation.

```
version: "3.3"
services:
  db:
    image: mariadb:10.6.4-focal
    command: '--default-authentication-plugin=mysql_native_password'
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      - MYSQL_ROOT_PASSWORD=somewordpress
      - MYSQL_DATABASE=wordpress
      - MYSQL_USER=wordpress
      - MYSQL_PASSWORD=wordpress
    expose:
      - 3306
      - 33060
  wordpress:
    image: wordpress:latest
    ports:
      - 80:80
    restart: always
    volumes:
      - type: bind
        source: ./name-of-the-theme
        target: /var/www/html/wp-content/themes/name-of-the-theme
    environment:
      - WORDPRESS_DB_HOST=db
      - WORDPRESS_DB_USER=wordpress
      - WORDPRESS_DB_PASSWORD=wordpress
      - WORDPRESS_DB_NAME=wordpress
volumes:
  db_data:
```

