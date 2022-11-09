# Tomcat

This directory contains information about installations for Tomcat 

### Installation

***Note :***  Ubuntu use `apt` not `yum`, `yum` is for **redhat** or **centos**

#### Steps

1. Change Hostname [ Best Practice ] 
```shell
$ sudo hostname tomcat-web01
``` 
change `tomcat-web01` with the hostname of your choice.
2. Install dependencies (Git, Wget, Java and Unzip)
use the command below to install **Git**, **Wget** and **Unzip**
```shell
$ cd /opt
$ sudo yum install git wget unzip 
```
Verify Git is installed correctly by using this command
```shell
$ git --version
```
check if Wget is installed correctly by using this command
```shell
$ which wget
```
check if Unzip is installed correctly by using this command
```shell
$ which unzip
```
Installing Java runtime
```shell
$ sudo yum install java-17-openjdk java-17-openjdk-devel -y 
```
Verify Java is correctly by using this command
```shell
$ Java --version
```
3. Download Tomcat zip & extract, Tomcat can be downloaded using this command.
```shell
$ sudo wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.68/bin/apache-tomcat-9.0.68.tar.gz 
```
To verify download was successful
```shell
$ ls
```
To Extract / Unzip 
```shell
$ sudo tar -xvf apache-tomcat-9.0.68.tar.gz
```
To verify extract was successful (you should see 2 files)
```shell
$ ls   
```
To remove zip file
```shell
$ sudo rm -rf apache-tomcat-9.0.68.tar.gz
```
To rename new unzipped file
```shell
$ sudo mv apache-tomcat-9.0.68/ tomcat9/
```
4. Change permission for tomcat - give full access

Give rwx for owner, group and other
```shell 
$ sudo chmod 777 -R /opt/tomcat9
```
Change owner of folder to ec2-user
```shell
$ sudo chown ec2-user -R /opt/tomcat9
```
Verify Permissions and Ownership
```shell
$ ls -l
```
Run tomcat startup script
```shell
$ sh /opt/tomcat9/bin/startup.sh
```
Create a soft link for the tomcat start & stop script
```shell
$ sudo ln -s /opt/tomcat9/bin/startup.sh /usr/bin/starttomcat 
$ sudo ln -s /opt/tomcat9/bin/shutdown.sh /usr/bin/stoptomcat
``` 
**Note :** Make sure to use absolute path

start tomcat with new soft link
```shell
$ starttomcat
```
Verify tomcat process running
```shell
$ ps -ef | grep tomcat
```
5. Access tomcat startup page

`http://<public-IP>:8080`
