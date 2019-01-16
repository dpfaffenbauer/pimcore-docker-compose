# Docker-Compose for Pimcore 5
Simple and easy Docker-Compose configuration for Pimcore 5.

Docker-Compose consists of following images:
 - Redis
 - MariaDB 10.1
 - httpd (Apache 2.4) & PHP-FPM with PHP7.1 and all Pimcore required dependencies (LibreOffice, FFMPEG, Image Libraries, etc)
 - PHP-FPM with PHP7.0 and all Pimcore required dependencies (LibreOffice, Image Libraries, etc) (except FFMPEG)
 
## Getting Started
### Requirements
* git
* docker
* docker-compose
### Checkout Repo
```bash
git clone https://github.com/dpfaffenbauer/pimcore-docker-compose.git
cd pimcore-docker-compose/
 ```
### Run Containers
```bash
# initialize and startup containers
docker-compose up
```
### Install Pimcore 
Choose which package to install https://pimcore.com/docs/5.x/Development_Documentation/Getting_Started/Installation.html#page_Choose-a-package-to-install
```bash
# get shell in running container
docker exec -it pimcore-php bash

# replace <yourpackage> with the package you with to install
# for example COMPOSER_MEMORY_LIMIT=-1 composer create-project pimcore/demo-ecommerce tmp
COMPOSER_MEMORY_LIMIT=-1 composer create-project pimcore/<yourpackage> tmp
mv tmp/* .  

#increase the memory_limit to >= 512MB as required by pimcore-install
echo 'memory_limit = 512M' >> /usr/local/etc/php/conf.d/docker-php-memlimit.ini;
service apache2 reload

#run installer
./vendor/bin/pimcore-install --mysql-host-socket=db --mysql-username=pimcore --mysql-password=pimcore --mysql-database=pimcore 

 ```

### Use
After the installer is finished, you can open in your Browser:
* Frontend: http://localhost:2000
* Backend: http://localhost:2000/admin
