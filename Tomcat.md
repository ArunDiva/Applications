Apache Tomcat is a free and open-source software, that acts as both a web server and a servlet container, enabling the execution of Java code and Java-based applications.

# PREREQUISITES

EC2 instance with your choice of Amazon Linux or Ubuntu is prepared for Tomcat deployment by opening port 8080 in the security group.

# JAVA INSTALLATION

_For Amazon Linux_

sudo su - 
yum install java-openjdk11=latest -y (For Amazon Linux)

_For Ubuntu_

sudo apt update
sudo apt install openjdk-11-jre-headless

# TOMCAT INSTALLATION

_switching to the root user_

sudo su or su -i

_This command changes the directory to /opt._

cd /opt

_This command uses the wget tool to download a file from the internet._

wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.86/bin/apache-tomcat-9.0.86.tar.gz

_This command extracts the downloaded archive using the tar tool._

tar -xvzf apache-tomcat-9.0.86 

_This command renames the extracted folder apache-tomcat-9.0.86 to a simpler name tomcat9._

mv apache-tomcat-9.0.86 tomcat9

# START AND STOP THE TOMCAT SERVER

_Execute the below command to change to bin directory in tomcat9_
cd /opt/tomcat9/bin/

_And using the below commands we can start and stop the tomcat9 server._
sh startup.sh or ./startup.sh
sh shutdown.sh or ./shutdown.sh

# CHANGE THE BELOW SETTINGS TO TOMCAT

_Change the directory to /opt/tomcat9_

cd tomcat9

_We need to find Content.xml file and comment the value tag below lines as shown in the image._

find -name context.xml

_Below files will be visible_

./conf/context.xml
./webapps/examples/META-IbbbbNF/context.xml
./webapps/host-manager/META-INF/context.xml
./webapps/manager/META-INF/context.xml

_ Comment value tag sections in below all files_

vi ./webapps/examples/META-INF/context.xml
vi ./webapps/host-manager/META-INF/context.xml
vi ./webapps/manager/META-INF/context.xml

# TOMCAT USER INFORMATION UPDATE

__Change the directory to /opt/tomcat9

cd apache-tomcat9/conf

__Open tomcat9 user xml file and update the username and password

vi tomcat-users.xml

__Add below lines between <tomcat-users> tag

<role rolename="manager-gui"/>
<user username="tomcat9" password="tomcat9pass" roles="manager-gui"/>

# TOMCAT WELCOME PAGE

_Use Ec2 instance pubic Ip address by using port 8080 and hit _
 
http://ip-address:8080/

_Tomcat9 welcome page will be displayed._ 

# YOU CAN ACCESS SERVER STATUS, MANAGER APP, AND HOST MANAGER BY ENTERING TOMCAT USERNAME AND PASSWORD

_We have changed the username and password in tomcat-users.xml file. Click on Manager App_

username="tomcat9" 
password="tomcat9pass"
