# Jenkins-installation
## This Directory contains information about how to install Jenkins

1. Hostname

     i. This command changes the hostname of the system to **jenkins**
     
     ```shell
     $ sudo hostnamectl set-hostname Jenkins
     ```

2. Install dependencies

     i. cd to opt & install wget and unzip
     
     ```shell
     $ cd /opt => go to opt dir
     $ sudo yum install wget unzip -y
     ```
    
3. Install Java using the links below
    
      i. Install Java JDK 1.8 min required
      
      
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
    
4. import Jenkins key & install jenkins repo in yum repo

   ```shell
   $ sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
   cd /etc/yum.repos.d/
   $ sudo curl -O https://pkg.jenkins.io/redhat-stable/jenkins.repo
   
5. Install Jenkins 

   ```shell
   $ sudo yum -y install jenkins  --nobest
   note: nobest will force installation even if not best option (req)
   ```
   
6. Start Jenkins svc 

   ```shell
   $ sudo systemctl start jenkins
   $ sudo systemctl enable jenkins
   $ sudo systemctl status jenkins
   ```

7. Access Jenkins

   ```shell
   http://<public-p>:8080
   ```
   
8. Get admin password

   ```shell
   $ sudo cat
   $ /var/lib/jenkins/secrets/initialAdminPassword
   ```
   
9. Verify jenkins running

   ```shell
   $ curl -v localhost:8080
   ```
