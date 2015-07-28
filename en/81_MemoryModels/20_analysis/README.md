# Analysis

## apache driven PHP webapp

![Figure 1: Apache PHP Memory Model](apache_php_memory_model.png) 

### Memory / Thread
1. The apache thread itself will take some memory - we measured about 8M per plain thread.
2. The payload php-thread can grow to his configured memory_limit - 256M in our case.

### Max Memory consumption
The overall memory consumption results in memory / thread * MaxClients (4 in our case).

### Articles to read
* http://jessesnet.com/development-notes/2014/apache-prefork-mpm-maxclients/
* https://www.devside.net/articles/apache-performance-tuning
* https://www.thomas-krenn.com/de/wiki/Apache_Performance_Tuning