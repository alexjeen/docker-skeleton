# Docker skeleton
docker skeleton for creating a controlled environment for php applications

# Introduction
With this skeleton you can easily create a webserver with a mysql database using docker-compose
This skeleton also links a phpmyadmin to the database so you can manage what is inside the database.
Also, no emails will be sent from this container, but catched by mailcatcher.
In this way you can easily test your projects without accidentally sending emails to your customers.

# Prerequisites
- 64 bit operating system
- Docker (https://www.docker.com/products/docker)

# Usage
1. Download or checkout this repository.
2. In the "Data" directory download the DataBrydge_AWS repository.
3. Open a terminal and navigate to the skeleton.
4. Create volume for mongodb `docker volume create --name=mongodata`
5. run `docker-compose up --build` or `docker-compose up -d` to run in background after first build
6. Windows. Need to add to hosts file 
   - 127.0.0.1 databrydge.test
   - 127.0.0.1 dataswitcher.test
   
7. After docker completed downloading all images, the services will run
8. Download databrydge_aws and dataswitcher_aws in the data directory.
9. If you want to run commands in the app container use command `docker exec -i -t dbg_console bash` to open a terminal open within the docker container. Then use `cd` to switch to the working project folder. From there run commands as if on a local environment.
10. To connect to mysql within the application use as ip address `mariadb`, for mongodb use `mongodb`
11. To connect to mysql / mongodb from outside the docker application use `localhost` / `127.0.0.1` 

# Configuration
## Database
The database settings can be changed in docker-compose.yml
## Webserver (php-apache)
You can change the php configuration in the services/php-apache/config/ folder.
Any .ini files you put here, will be loaded in php.
After changing any of the ini files, you'll need to rebuild. `docker-compose up --build`


# Default configuration
The default configuration for the database is as follows:
- hostname: db
- root password: root
- user: db
- password: db
- database: db

# Ports
Docker compose will start the following services
You can access these services from a browser.
For example:
http://localhost:80 for the webserver

1. The webserver (port: 80)
2. Phpmyadmin (port: 8181)
3. Mailcatcher (port: 1080)

