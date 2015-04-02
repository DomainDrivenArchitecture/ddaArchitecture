# Analysis

## Whiteboard
* https://awwapp.com/draw.html#a349121d

## Tools
* Project: http://d2rq.org/
* Code: https://github.com/d2rq/d2rq

## Idea
* Multisource ability by using war files. The war file will define the url namespace ...

## Solution
* Path on Server: /var/lib/d2rq-0.8.1
* Start: ./d2r-server -b http://iwbdemo.meissa-gmbh.de:2020/ mapping_part_shj.ttl
* 

### Setup DB
mysql -hlocalhost -uroot -prootpwd -e "CREATE USER 'pa_user'@'localhost' IDENTIFIED BY 'wwwjfurt'";
mysql -hlocalhost -uroot -prootpwd -e "CREATE DATABASE IF NOT EXISTS pa_portal";
mysql -hlocalhost -uroot -prootpwd -e "GRANT ALL ON pa_portal.* TO 'pa_user'@'localhost'";
mysql -hlocalhost -uroot -prootpwd -e "FLUSH PRIVILEGES";
 
  # replace location in portal config
   
mysql -hlocalhost -upa_user -pwwwjfurt pa_portal < output2.sql



./generate-mapping -u pa_user -p wwwjfurt -o mapping_pa_portal_full.ttl jdbc:mysql://127.0.0.1:3306/pa_portal
./d2r-server -b http://iwbdemo.meissa-gmbh.de:2020/ mapping_pa_portal_full.ttl
  
 

