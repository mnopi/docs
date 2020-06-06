# Jenkins
## [Getting Started](https://jenkins.io/doc/pipeline/tour/getting-started/)
```shell script
jenkins
e8480bc42c6a45e3acf05f450d6c2c4d
/Users/j5pu/.jenkins/secrets/initialAdminPassword
open http://localhost:8080
```
```shell script
java -jar jenkins.war --httpPort=8080
```
Error con plugin de jenkins
```
@xros Since Jenkins 2.176 the CSRF handling was improved. The the crumb not work anymore with different session.
We could change the code to handle an own session. But i think it is better to use an API token for authenticate the plugin.
To do this do following:

Got to your user setting: http://:8080/user//configure
Add New API Token for Jenkins Plugin
Use this API Token as your Password
```
