# SonarQube
The directory contains information about installations for SonarQube 7.8
## Installation

### STEPS
1. Hostname

     i. This command changes the hostname of the system to **sonar**
     
     ```shell
     $ sudo hostnamectl set-hostname sonar
     ```
     
2. Create sonar user. Make user Admin & Super user

     i. Create user
     
     ```shell
    $ sudo useradd sonar
    ```
    
    ii. Give sudo permission
    
    ```shell
    $ sudo echo "sonar ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/sonar
    ```
    
    iii. Switch to become user
    
    ```shell
    $ su - sonar
     ```

3. Install dependencies

     i. cd to opt & install wget and unzip (note it wont install in /opt its a yum package)
     
    ```shell
    $ cd /opt => go to opt
    $ sudo yum install wget unzip -y
    ```
    
    ii. Make sure wget has been installed
    ```shell
    $ which wget
    ```
    
    iii. Check if Unzip is installed correctly by using the command below
    ```shell
    $ which unzip
    ```
    
4. Install Java using the links below

    i. Install Java JDK 1.8 min required
    
    ```shell
    $ sudo yum install java-11-openjdk-devel java-1.8.0-openjdk-devel -y
    ```

    ii. Verify Java Version
    
    ```shell
    $ java -version 
    ```
    
5. Download SonarQube 7.8 from site with tar /zip url

    ```shell
    $ sudo wget sudo wget [http://download.sonartype.com/nexus/3/nexus-3.15.2-01-unix.tar.gz](http://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-7.8.zip)
    ```
    
6. Unzip file downloaded

    ```shell
    $ sudo unzip sonarqube-7.8.zip
    ```
    
7. Remove Zip and Rename the file
     
     i. Remove zip file
     
    ```shell
    sudo 
    $ sudo rm -rf sonarqube-7.8.zip
    ```
    
    ii. Rename file
    ```shell
    $ mv sonarqube-7.8/ sonnarqube
    ```
    
8. Permissions. Change group & owner of directory to 775 permission.

     i. Gives read, write, and execute permissions to the owner, read and execute permissions to members of the owner's group, and no permissions to all other users.
     
    ```shell
    $ sudo chown -R sonar:sonar /opt/sonarqube
    $ sudo chmod -R 775 /opt/sonarqube
    ```
    
9. Start Sonarqube

    ```shell
    $ sh /opt/sonarqube/bin/linux.../sonar.sh start
    {sonar.sh stop. sonar.sh restart}
    ```
   
10. Access on Port 9000 in browser

    ```shell
    http://<your-external-ip>:9000
    ```
