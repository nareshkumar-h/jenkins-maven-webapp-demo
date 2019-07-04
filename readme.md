#### Install Tomcat in EC2 instance
* Tomcat 9.0

#### Download and Extract
*  sudo wget http://mirrors.advancedhosters.com/apache/tomcat/tomcat-9/v9.0.21/bin/apache-tomcat-9.0.21.tar.gz
*  tar -zxvf apache-tomcat-9.0.21.tar.gz  

#### Update manager app - webapps/manager/META-INF/context.xml
* Comment RemoteAddr section to access tomcat from Jenkins
```
<Context antiResourceLocking="false" privileged="true" >
<!--  <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
  <Manager sessionAttributeValueClassNameFilter="java\.lang\.(?:Boolean|Integer|Long|Number|String)|org\.apache\.catalina\.filters\.CsrfPreventionFilter\$LruCache(?:\$1)?|java\.util\.(?:Linked)?HashMap"/>
-->
</Context>
```

#### Add user in tomcat ( conf/tomcat-users.xml)
```
<user username="naresh" password="naresh" roles="manager-script" />
```
Note :
* The above username/password needs to be entered in Jenkins to Deploy war in Tomcat


#### Create a Webhook  in Github for Project Repository
* Settings/ Webhook => Add Webhook
* Payload URL : http://ec2-34-224-214-24.compute-1.amazonaws.com:8080/github-webhook/  ( Jenkins Server URL )
* Content Type : application/json
* Secret: 
* Events : push 



