# How to Install JDK and Tomcat on Windows 11 (Local webserver setup for development and testing)
Step by Step Guide.

This will setup a webserver on your machine which can used to launch and test your web applications. 
This will help for development, dev testing, demo and even product level testing before going live.

## JDK Download and Setup
First Let us Install JDK:
https://www.oracle.com/java/technologies/downloads/#jdk21-windows
OR
https://www.oracle.com/java/technologies/downloads
Go to windows tab and download x64 Installer
Double Click to install.

Go to the install path and copy the **bin** path.
Typically:
C:\Program Files\Java\jdk-21\bin

**Let us set the env variables.**
Go to start->search env variables setting
Advanced->Environment Variables click
System Variables
Select Path
Edit
New
Paste : C:\Program Files\Java\jdk-21\bin
Click ok

**Under System Variables, click new**
Variable Name : JAVA_HOME
Variable Value : C:\Program Files\Java\jdk-21

**JDK setup completed.**
**------------------**

## Tomcat Download and Setup
**Download Tomcat**
https://tomcat.apache.org/download-10.cgi
64-bit Windows zip (pgp, sha512)
Download
Extract.

**You can rename the outer folder removing all sub versions like apache-tomcat-10**
Copy the complete folder to C: drive
Go inside and copy the complete bin path:
Typically:
C:\apache-tomcat-10\apache-tomcat-10.1.19\bin

**Let us set the env variables.**
Go to start->search env variables setting
Advanced->Environment Variables click
System Variables
Select Path
Edit
New
Paste : C:\apache-tomcat-10\apache-tomcat-10.1.19\bin
Click ok

**Under System Variables, click new**
Variable Name : CATALINA_HOME
Variable Value : C:\apache-tomcat-10\apache-tomcat-10.1.19

**RUN: startup.bat from**
C:\apache-tomcat-10\apache-tomcat-10.1.19\bin
(Either from commandline or right click run as administrator)

**Open Internet Browser
Type and enter:
localhost:8080**

**Will open tomcat page successfully showing the server status, manager app, host manager etc.**

Now:
RUN: shutdown.bat from
C:\apache-tomcat-10\apache-tomcat-10.1.19\bin
(Either from commandline or right click run as administrator)

## To configure users for manager app and Host manager in tomcat.
Open:
"C:\apache-tomcat-10\apache-tomcat-10.1.19\conf\tomcat-users.xml"

Add the following two users at the last (before </tomcat-users> line)
<role rolename="manager-gui"/>
<user username="tomcatm" password="password" roles="manager-gui"/>

<role rolename="admin-gui"/>
<user username="tomcata" password="password" roles="admin-gui"/>

You can update the rolename, username, password and roles as needed.

RUN: startup.bat from
C:\apache-tomcat-10\apache-tomcat-10.1.19\bin
(Either from commandline or right click run as administrator)

Open Internet Browser
Type and enter:
localhost:8080

Now using the above users you can login to manager app (with tomcatm user) and host manager (using tomcata user)

Now you have completed tomcat installation, running and user configurations.

