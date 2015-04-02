# Analysis

## Overview

![](ontology.png)

## Tools
* Project: http://d2rq.org/
* Code: https://github.com/d2rq/d2rq
* Path on Server: /var/lib/d2rq-0.8.1

## Idea
* Establish a multi-source ability by deploying .war-files into a servlet container (e.g. tomcat), running on a server
* use a distinct .war-file for every business application
* thus, databases that do not belong together stay separated
* when accessing the the server, the client application can be accessed by the URL which contains the name of the .war-file
* thus, the URLs define namespaces for different business applications

## Solution

### Setup DB
e.g. for sql-backup-file named "output2.sql" with [username], [userPassword] and [dbName] for D2RQ on [server]

* mysql -hlocalhost -uroot -prootpwd -e "CREATE USER '[username]'@'localhost' IDENTIFIED BY '[userPassword]'";
* mysql -hlocalhost -uroot -prootpwd -e "CREATE DATABASE IF NOT EXISTS [dbName]";
* mysql -hlocalhost -uroot -prootpwd -e "GRANT ALL ON [dbName].* TO '[username]'@'localhost'";
* mysql -hlocalhost -uroot -prootpwd -e "FLUSH PRIVILEGES";
* mysql -hlocalhost -u[username] -[userPassword] [dbName] < output2.sql
 
### Generate Mapping
* ./generate-mapping -u [username] -p [userPassword] -o mapping_[dbName]_full.ttl jdbc:mysql://127.0.0.1:3306/[dbName]

### Start Server with Jetty
* ./d2r-server -b http://[server]:2020/ mapping_[dbName]_full.ttl

  
 

