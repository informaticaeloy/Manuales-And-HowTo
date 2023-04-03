# ThePhish-Installation

usuario@ubuntu:~$ java --version

Command 'java' not found, but can be installed with:

> sudo apt install default-jre              # version 2:1.11-72, or

 sudo apt install openjdk-11-jre-headless  # version 11.0.15+10-0ubuntu0.20.04.1

 sudo apt install openjdk-13-jre-headless  # version 13.0.7+5-0ubuntu1~20.04

 sudo apt install openjdk-16-jre-headless  # version 16.0.1+9-1~20.04

 sudo apt install openjdk-17-jre-headless  # version 17.0.3+7-0ubuntu0.20.04.1

 sudo apt install openjdk-8-jre-headless   # version 8u312-b07-0ubuntu1~20.04 <

```shell
sudo apt install default-jdk
```

```shell
sudo -v ; wget -q -O /tmp/install-thehive.sh https://archives.strangebee.com/scripts/install-deb.sh ; bash /tmp/install-thehive.sh

```
![image](https://user-images.githubusercontent.com/20743678/182606204-7d1c61d7-ac05-4f6e-a899-b09fe3a1c8ce.png)

![image](https://user-images.githubusercontent.com/20743678/182607507-b9834134-1e7f-412d-8ab3-9d52c9a4b11a.png)


![image](https://user-images.githubusercontent.com/20743678/182128531-fcc82ec5-8b80-45bb-92b8-863cfb61d1bf.png)

usuario@ubuntu:~/Desktop$ wget -q -O /tmp/install-thehive.sh https://archives.strangebee.com/scripts/install-deb.sh 
usuario@ubuntu:~/Desktop$ bash /tmp/install-thehive.sh
---
THeHive installation script for Linux using DEB packages

Following softwares will be installed:
 - Cassandra 4.0.x
 - Elasticsearch 7.x
 - TheHive 5.x
 
It has sucessfully been tested on freshly installed Operating systems:
 - Ubuntu 20.04 LTS
 - Debian 11

Requirements: 
 - 4vCPU
 - 16 GB of RAM
 
Usage:
 
   $ sudo -v && bash install-deb.sh 
 

Maintained by: ©StrangeBee - https://www.strangebee.com

---


Installing package(s) wget gnupg apt-transport-https
[sudo] password for usuario: 
  package(s) wget gnupg apt-transport-https installed
Installing package(s) openjdk-11-jre-headless
  package(s) openjdk-11-jre-headless installed
Installing package(s) cassandra
 package(s) cassandra installed
Configuring cassandra
Installing package(s) elasticsearch
  package(s) elasticsearch installed
Configuring elasticsearch
Installing package(s) thehive
  package(s) thehive installed
Configuring thehive

Starting services
  * Service cassandra is starting
  * Service elasticsearch is starting
  * Service thehive is starting
>>>> TheHive installation complete! More information is available in /tmp/install-thehive.log file.

![image](https://user-images.githubusercontent.com/20743678/182614300-3c1caeaa-da1e-49bf-8c98-2de07e529a65.png)

