# TimeOuts on three Tier Web Applications

In three tier architectures (web server - app server - db server) it's important to do a fine configuration of timeouts, maximum requests and connection pools. If timeouts get lost, the danger is, to get broken connections and resulting loss of performance. Analysis of timeout caused issues is a hard job.

Therefore, the main idea is:

**Build a hopper which has its tightest point on web server.**

Following this idea, our connections will stay stable thru all involved systems and tiers.

## Web Tier
The web tier has to limit the load of the whole system.

### /etc/apache2/conf-enabled/limits.conf
```
ServerLimit 150
MaxClients  150
```

### /etc/apache2/sites-enabled/000-default-ssl.conf
```
JkMount /* mod_jk_www
```

### /etc/libapache2-mod-jk/httpd-jk.conf 

```
JkStripSession On
JkWatchdogInterval 120
```
  

### /etc/libapache2-mod-jk/workers.properties

```
worker.list=mod_jk_www
worker.maintain=60

# connection to app server
worker.mod_jk_www.port=8009
worker.mod_jk_www.host=127.0.0.1
worker.mod_jk_www.type=ajp13

#for use with firewalls
#worker.mod_jk_www.socket_keepalive=true

# timeouts
worker.mod_jk_www.socket_connect_timeout=300
worker.mod_jk_www.socket_timeout=60000

```

### Reference
* https://tomcat.apache.org/connectors-doc/reference/apache.html
* https://tomcat.apache.org/connectors-doc/common_howto/timeouts.html
* https://tomcat.apache.org/connectors-doc/reference/workers.html

## App Tier
App tier does the business logic. Tomcats threadpool should be large enough to handle incoming requests and configured additional (qartz?) jobs.   

### /etc/tomcat7/server.xml

```
<Server>
  <Service name='Catalina'>
     <Executor name='tomcatThreadPool' maxThreads="161"/>
    <Connector executor="tomcatThreadPool" protocol="AJP/1.3" connectionTimeout="61000"
maxThreads="151" />
```

### portal-ext.properties

```
#
# C3PO
#
jdbc.default.idleConnectionTestPeriod=60
jdbc.default.maxIdleTime=3600
jdbc.default.maxPoolSize=152
jdbc.default.minPoolSize=40
#
# Quartz configuration
#
org.quartz.threadPool.threadCount=10

```

### Refernce
* https://tomcat.apache.org/tomcat-7.0-doc/config/ajp.html
* https://www.liferay.com/de/community/wiki/-/wiki/Main/Database+Portal+Properties

## Db Tier
Sizing DB Connections is not as easy as sizing tomcats thread pool, as the number of needed DB connection per http request will depend on used application. Lets assume, that our portlets have an average rate DB-connection to http request of 1:1 (you've to measure your ratio by your own statistic analysis). 
  
### /etc/mysql/my.cnf

```
max_connections= 153
net_read_timeout=62
net_write_timeout=62
```

### Reference
* https://dev.mysql.com/doc/refman/5.7/en/




