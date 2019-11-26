# APM-plugin-userguide
SnappyFlow APM plugin on-boarding user guide

Apache agent plugin

Prerequisites:
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
      
  
     
