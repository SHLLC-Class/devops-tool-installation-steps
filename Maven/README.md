# Maven

This directory contains information about installations for Maven 

### Installation

***Note :***  Ubuntu use `apt` not `yum`, `yum` is for **redhat** or **centos**

#### Steps

1. Change Hostname [ Best Practice ] 
```shell
$ sudo hostname maven-build01
``` 
change `maven-build01` with the hostname of your choice.
2. Install dependencies (Git, Java, Unzip)
   1. use the command below to install **Git**, **Wget** and **Unzip**
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
   4. Installing Java runtime
    ```shell
    $ sudo yum install java-17-openjdk java-17-openjdk-devel -y 
    ```
   5. Verify Java is correctly by using this command
    ```shell
    $ Java --version
    ```
3. Download Maven zip & extract
   1. Maven can be downloaded using this command.
   ```shell
       $ sudo wget https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.zip 
   ```
   2. To verify download was successful
   ```shell
      $ ls
   ```
   3. To Extract / Unzip 
   ```shell
   $ sudo unzip apache-maven-3.8.6-bin.zip 
   ```
   4. To verify extract was successful (you should see 2 files)
   ```shell
   $ ls   
   ```
   5. To remove zip file
   ```shell
   $ sudo rm -rf apache-maven-3.8.6-bin.zip
   ```
   6. To rename new unzipped file
   ```shell
   $ sudo mv apache-maven-3.8.6/ maven
   ```
4. Set up user env var - bash profile

   1. Open bash_profile
   ```shell 
   $ vi ~/.bash_profile
   ```
   2. Add env variable to the bash_profile (use path to maven binary) 
   ```shell
   export M2_HOME=/opt/maven
   export PATH=$PATH:$M2_HOME/bin
   ```
   3. Save & quit vi
   ```shell
   :wq!
   ```
   4. Refresh bash_profile 
   ```shell
   $ Source ~/.bash_profile
   ```
   5. Verify Maven path =>
      1. ```shell
          $ echo $M2_HOME
         ```
         should print `/opt/maven `
      2. ```shell
         $ echo $PATH
         ```
         should have ..`:/opt/maven/bin`
5. Verify Maven is installed correctly by using this command 
```shell
mvn - version
```

**Note :** Path is a list of dir locations where Linux & windows will look whenever you type a command. Meaning if a command binary is in a location not listed in path, the command will not execute. Think of it like a library of commands