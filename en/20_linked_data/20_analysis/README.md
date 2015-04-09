# Analysis

## Overview and Basics
![](linkedData_ontology.png)


### Underlying Structure and Procedure
* D2RQ-Server is running on machine, using either Jetty or a servlet container (e.g. tomcat) 
* Server contains mapping of a database (created beforehand)
* Machine is then accessed via http protocol in web-browser
* RFD-data can be requested from D2RQ Server
* yields view of RDF-structured linked data
* SPARQL queries are supported by D2RQ
* Browser may send SPARQL queries

### Development Procedure:
* Assuming a running server (e.g. localhost) with D2RQ-Server
* Setup underlying Database
* Create full Mapping
* Reduce Mapping (when necessary): Extract relevant data
* Start D2RQ-Server with Mapping
* Use SPARQL queries to access data in browser


## Tools
* Project: http://d2rq.org/
* Code: https://github.com/d2rq/d2rq
* Path on Server: /var/lib/d2rq-0.8.1

## Idea: Multi-Source Ability
* Establish a multi-source ability by deploying .war-files into a servlet container (e.g. tomcat), running on a server
* use a distinct .war-file for every business application
* thus, databases that do not belong together stay separated
* when accessing the the server, the client application can be accessed by the URL which contains the name of the .war-file
* thus, the URLs define namespaces for different business applications

## Solution
for single business application

### Setup DB
* e.g. for sql dump file named "output2.sql"
* authorization via: [username], [userPassword] and [dbName] for D2RQ on running [server]

    1. Create DB user:
    
    mysql -hlocalhost -uroot -prootpwd -e "CREATE USER '[username]'@'localhost' IDENTIFIED BY '[userPassword]'";
    2. Create DB: 
    
    mysql -hlocalhost -uroot -prootpwd -e "CREATE DATABASE IF NOT EXISTS [dbName]";
    3. Set permission:
    
    mysql -hlocalhost -uroot -prootpwd -e "GRANT ALL ON [dbName].* TO '[username]'@'localhost'";
    4. Reload grant tables
    
    mysql -hlocalhost -uroot -prootpwd -e "FLUSH PRIVILEGES";
    5. Load DB
    
    mysql -hlocalhost -u[username] -[userPassword] [dbName] < output2.sql
 

### Generate full Mapping
* ./generate-mapping -u [username] -p [userPassword] -o mapping_[dbName]_full.ttl jdbc:mysql://127.0.0.1:3306/[dbName]

### Adapt full Mapping
* vi mapping_[dbName]_full.ttl
* extract necessary fields
* make sure to delete fields relevant to security (plain text passwords, answers to security questions, etc.)
* Terminology of Ontology:
* Triples of subject, predicate and object:
* subject: instance of a class
* predicate: RDF property 
* object: value of RDF property

### Start Server with Jetty
* ./d2r-server -b http://[server]:2020/ mapping_[dbName]_full.ttl

### Access Linked Data via SPARQL query
* access SPARQL on running server in browser
* e.g. localhost:8080/sparql
* run SPARQL queries
* optional: set limit (number of results shown)
* review results

  
 

