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
use the commands below to install **Git**, **Wget** and **Unzip**
    1. 
   ```shell
    $ cd /opt
    $ sudo yum install git wget unzip 
    ```
    2. Verify Git is installed correctly by using this command
    ```shell
    $ git --version
    ```
    3. check if Wget is installed correctly by using this command
    ```shell
    $ which wget
    ```
    4. check if Unzip is installed correctly by using this command
    ```shell
    $ which unzip
    ```
    5. Installing Java runtime
    ```shell
    $ sudo yum install java-17-openjdk java-17-openjdk-devel -y 
    ```
    6. Verify Java is correctly by using this command
    ```shell
    $ Java --version
    ```
3. Download Tomcat zip & extract, 

   1. Tomcat can be downloaded using this command.
    ```shell
    $ sudo wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.68/bin/apache-tomcat-9.0.68.tar.gz 
    ```
    2. To verify download was successful
    ```shell
    $ ls
    ```
    3. To Extract / Unzip 
    ```shell
    $ sudo tar -xvf apache-tomcat-9.0.68.tar.gz
    ```
    4. To verify extract was successful (you should see 2 files)
    ```shell
    $ ls   
    ```
    5. To remove zip file
    ```shell
    $ sudo rm -rf apache-tomcat-9.0.68.tar.gz
    ```
    6. To rename new unzipped file
    ```shell
    $ sudo mv apache-tomcat-9.0.68/ tomcat9/
    ```
4. Change permission for tomcat - give full access

    1. Give rwx for owner, group and other
    ```shell 
    $ sudo chmod 777 -R /opt/tomcat9
    ```
    2. Change owner of folder to ec2-user
    ```shell
    $ sudo chown ec2-user -R /opt/tomcat9
    ```
    3. Verify Permissions and Ownership
    ```shell
    $ ls -l
    ```
    4. Run tomcat startup script
    ```shell
    $ sh /opt/tomcat9/bin/startup.sh
    ```
    5. Create a soft link for the tomcat start & stop script
    ```shell
    $ sudo ln -s /opt/tomcat9/bin/startup.sh /usr/bin/starttomcat 
    $ sudo ln -s /opt/tomcat9/bin/shutdown.sh /usr/bin/stoptomcat
    ``` 
    **Note :** Make sure to use absolute path

    6. Start tomcat with new soft link
    ```shell
    $ starttomcat
    ```
    7. Verify tomcat process running
    ```shell
    $ ps -ef | grep tomcat
    ```
   
5. Access tomcat startup page

`http://<public-IP>:8080`
