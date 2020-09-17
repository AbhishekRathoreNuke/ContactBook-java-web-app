# ContactBook-java-web-app

Sample Java Web App 


Contact Book 
---------------------------
Just to store Name and Contact no. in database and then retrieve it back.



Deployment of this project on AWS EC2 video available on Youtube > https://youtu.be/Mkm7HQkVOfk
Deployable .war file > https://drive.google.com/open?id=1AoOjHWdmim1865emG1FPAop0zA4W7pPD

Procedure:
just deploy .war on tomcat server 
and host a local MySql-server with "student" database and "register" table with attribute "name" and "phoneno".

or modify source code according to you.


#HappyCoding

checkout my blog for more tutorials and tricks                       -
==========================================                           -
https://cyberhackersz.blogspot.com                                   -
------------------------------------------                           -
                                                                     -
Like facebook page                                                   -
==========================================                           -
https://facebook.com/cyberhackersz                                   -
--------------------------------------                               -
                                                                     -
clone source code of web app   (ContactBook)                         -
=================================                                    -
https://github.com/imayushsaini/ContactBook-java-web-app             -
----------------------------------------------------------------------


 tomcat server download 
==================================
https://tomcat.apache.org/download-90.cgi 
-----------------------------------

conf/tomcat-users.xml
==========================================
<role rolename ="manager-gui"/>
<role rolename="manager-script"/>
<user username="admin" password="12345678" roles="manager-gui,manager-script"/>
--------------------------------------------------

install/java
================================
sudo apt install default-jre
-------------------------------

conf/server.xml
============================================
<Context path="" docBase="ContactBook">

  <!-- Default set of monitored resources -->
  <WatchedResource>WEB-INF/web.xml</WatchedResource>

</Context>
-----------------------------------------------

install nginx
=========================================
sudo apt install nginx
----------------------------------------


configuring nginx to act as reverse proxy
=====================================
sudo rm /etc/nginx/sites-available/default
sudo nano /etc/nginx/sites-available/default

server {
    listen 80;    
      server_name 34.219.236.72;
     location / {
        proxy_pass http://172.31.59.60:8090;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
     }
}

sudo systemctl status nginx    
sudo systemctl start nginx
----------------------------------------------


installing mysql-server
================================
sudo apt install mysql-server
-----------------------------

changing root user password
=============================================
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '12345678';
-------------------------------------------------------------------
