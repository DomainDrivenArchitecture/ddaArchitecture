# apache driven java webapp

Dimensions are 
* filehandles, 
* http-requests, 
* tomcat threads, 
* quarz-jobs,
* db connections

6 Worker, 84 File Descriptors

The following commands were executed on the server: 

* lsof -a -p PID | wc -l (count of open file discriptors of the PID)
* apachetop -f /var/log/apache2/ssl-access.log
* top
* ls -l /proc/*/fd | wc -l (count of all open file discriptors)
* The command: watch -n1 "ls -l /proc/*/fd | wc -l" will print the count of all open file discriptors
and refresh every second

For further information/commands visit: http://www.cyberciti.biz/tips/linux-procfs-file-descriptors.html