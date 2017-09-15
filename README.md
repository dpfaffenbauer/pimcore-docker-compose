# Docker-Compose for Pimcore 5
Simple and easy Docker-Compose configuration for Pimcore 5.

Docker-Compose consists of following images:
 - Redis
 - MariaDB 10.1
 - httpd (Apache 2.4)
 - PHP-FPM with PHP7.1 and all Pimcore required dependencies (LibreOffice, FFMPEG, Image Libraries, etc)
 - PHP-FPM with PHP7.0 and all Pimcore required dependencies (LibreOffice, Image Libraries, etc) (except FFMPEG)