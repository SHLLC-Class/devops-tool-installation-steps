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
Installing Java runtime
```shell
$ sudo yum install java-17-openjdk java-17-openjdk-devel -y 
```
Verify Java is correctly by using this command
```shell
$ Java --version
```
3. Download Maven zip & extract, Maven can be downloaded using this command.
```shell
$ sudo wget https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.zip 
```
To verify download was successful
```shell
$ ls
```
To Extract / Unzip 
```shell
$ sudo unzip apache-maven-3.8.6-bin.zip 
```
To verify extract was successful (you should see 2 files)
```shell
$ ls   
```
To remove zip file
```shell
$ sudo rm -rf apache-maven-3.8.6-bin.zip
```
To rename new unzipped file
```shell
$ sudo mv apache-maven-3.8.6/ maven
```
4. Set up user env var - bash profile
Open bash_profile
```shell 
$ vi ~/.bash_profile
```
Add env variable to the bash_profile (use path to maven binary) 
```shell
export M2_HOME=/opt/maven
export PATH=$PATH:$M2_HOME/bin
```
Save & quit vi
```shell
:wq!
```
Refresh bash_profile 
```shell
$ Source ~/.bash_profile
```
Verify Maven path =>
```shell
$ echo $M2_HOME
``` 
should print `/opt/maven `
```shell
$ echo $PATH
```
should have ..`:/opt/maven/bin`
5. Verify Maven is installed correctly by using this command 
```shell
mvn - version
```

**Note :** Path is a list of dir locations where Linux & windows will look whenever you type a command. Meaning if a command binary is in a location not listed in path, the command will not execute. Think of it like a library of commands