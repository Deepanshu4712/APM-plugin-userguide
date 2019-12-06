# APM-plugin-userguide
SnappyFlow APM plugin on-boarding user guide

## Apache agent plugin

### Prerequisites:
1. Enable Response time in Apache access-logs as follows:

    a) Edit the apache configuration file. 
    
      For ubuntu :
      
        sudo vi /etc/apache2/apache2.conf
      
      For Centos/RHEL :
      
        sudo vi /etc/httpd/conf/httpd.conf
      
   b) Search for "LogFormat" and add '%D' at the end of the LogFormat. After adding, the LogFormat should be similar to:
     
        LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %D" <customFormatName>
      
   c) Save the file and restart the apache service.
   
      For Ubuntu:
      
        sudo service apache2 restart
      
      For Cent/RHEL:
      
        sudo service httpd restart
      
## Mongod agent plugin

### Prerequisites:
1. Create a dedicated read-only user to monitor the mongodb.

    a) In the Mongo Shell login to admin database:
          
          use admin:
          db.auth('username','UNIQUE_PASSWORD')
    b) In Mongo version > 3.X use the createUser command. Provide read access to database which is need to be monitored
           
           db.createUser({
                "user":"USERNAME",
                "pwd": "<UNIQUEPASSWORD>",
                "roles" : [
                {role: 'read', db: 'admin' },
                {role: 'clusterMonitor', db: 'admin'},
                {role: 'read', db: 'local' }
                ]
                })
    c) Authenticate with the created user Credentials and validate:
            
            db.auth('USERNAME','<UNIQUEPASSWORD>')
            
    d) Enable Profiler and set it to Level 1 for Slow Queries.Default slowms is 100ms.
    
            db.setProfilingLevel(1)
            
2. Provide this credentials in SnappyFlow APM to monitor your Mongod.
       
     
