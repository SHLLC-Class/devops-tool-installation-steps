# Nexus
## This Directory contains information about how to install Nexus
### Steps

### STEPS
1. Hostname

     i. This command changes the hostname of the system to **Nexus**
     
     ```shell
     $ sudo hostnamectl set-hostname Nexus
     ```
     
2. Create nexus user. Make user Admin & Super user

     i. Create user
     
     ```shell
    $ sudo useradd nexus
    ```
    
    ii. Give sudo permission
    
    ```shell
    $ sudo echo "nexus ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/nexus
    ```
    
    iii. Switch to become user
    
    ```shell
    $ su - nexus
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
    
5. Download Nexus 3.15.2 from site with tar/zip url

    ```shell
    $ sudo wget sudo wget https://download.sonatype.com/nexus/3/nexus-3.15.2-01-unix.tar.gz
    ```
    
6. Untar file downloaded

    ```shell
    $ sudo tar -xvf nexus-3.15.2-01-unix.tar.gz
    ```
    
7. Remove tar and Rename the file
     
     i. Remove tar file
     
    ```shell
    sudo 
    $ sudo rm -rf nexus-3.15.2-01-unix.tar.gz
    ```
    
     ii. Rename file
    
    ```shell
    $ sudo mv /opt/nexus-3.15.2-01 /opt/nexus
    ```
    
8. Permissions. Change group & owner of directory to 775 permission.

     i. Gives read, write, and execute permissions to the owner, read and execute permissions to members of the owner's group, and no permissions to all other users.
     
    ```shell
    $ sudo chown -R nexus:nexus /opt/nexus
    $ sudo chown -R nexus:nexus /opt/sonatype-work
    $ sudo chmod -R 775 /opt/sonarqube
    $ sudo chown -R 775 /opt/sonatype-work
    ```
    
9. Set run user_as_user to nexus. Allows nexus user to run nexus

    ```shell
    $ vi /opt/nexus/bin/nexus.rc
    run_as_user="nexus". ==> (remove the # to uncomment)
    ```
    
10. Configure Nexus to run as a service
     
     i. softlink the nexus program to init.d to register it with init daemon (Note: use absolute path)

    ```shell
    $ sudo ln -s /opt/nexus/bin/nexus /etc/init.d/nexus.   
    ```
       
11. Start Nexus
     
     i. Enable nexus service
     
    ```shell
    sudo 
    $ sudo systemctl enable nexus 
    ```
    
     ii. Start nexus service
    
    ```shell
    $ sudo systemctl start nexus 
    ```
   
      iii. Verify nexus service is active
    
    ```shell
    $ sudo systemctl status nexus 
    ```
    
12. Access on Port 8081 in browser

    ```shell
    http://<your-external-ip>:8081
    ```
