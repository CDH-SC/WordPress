# WordPress
---

This is a repository documenting the steps to create a network of Dockerized *Wordpress* instances on a single virtual machine. However, by replacing the docker-compose.yml file, many other containerized content managment systems can be substituted.

It will walk you through each of the required softwares, files, and DNS configurations to get it working.
We will be using Google Cloud Platform to host our VM and configure the DNS settings.

Table of Contents
* [Getting Started](#Getting-Started)
* [Configurations](#Configurations)
* [Deployment](#Deployment)
* [Testing and troubleshooting](#Testing-and-troubleshooting)
* [Credits](#Credits)

# Getting started
---
To create a working network of containers hosting wordpress sites, the host machine must have the following software installed.

| Software Homepage                                     |                Used for             |       Location    |
| ------------------------------------------------------|:-----------------------------------:| -----------------:|
| [Google Cloud Console](https://console.cloud.google.com/)     | Interface for booting up VMs        | Hosted by Google  |
| [Google Cloud DNS](https://console.cloud.google.com/net-services/dns/)         | Interface for configuring DNS       | Hosted by Google  |
| [Nginx](https://nginx.org/en/docs/)                        | Proxy on VM                         | Installed on VM   |
| [Certbot](https://certbot.eff.org/)                   | secure connections to containers    | Installed on VM   |
| [Docker CE](https://docs.docker.com/install/)  | daemon for running containers       | Installed on VM   |
| [Docker-compose](https://docs.docker.com/compose/)    | orchestraion of multiple Containers | Installed on VM   |



# Configurations

---

## **_Google Cloud Console_**
The [Google Cloud Console](<https://console.cloud.google.com/>) hosts a variety of tools, we will be using *VM instances* under the *Compute Engine* tab

![alt text](https://github.com/CDH-SC/WordPress/blob/master/README_images/ComputeEngine.png "ComputeEngine")

Click the ![create instance](https://github.com/CDH-SC/WordPress/blob/master/README_images/createInstance.png "create Instance button") button and configure the machine as needed. These are the configurations we used.

![alt text](https://github.com/CDH-SC/WordPress/blob/master/README_images/vmConfig.png "Configs")

Click the create vm, and make a note of the machines IP. The IP will be used when configuring the Cloud DNS records.

![alt text](https://github.com/CDH-SC/WordPress/blob/master/README_images/vmIP.png "Configs")



## **_Google Cloud DNS_**

Cloud DNS is where all of our routing records will be located.

## **_Nginx_**
Used on the machine to manage connections. Referencing the [exampleSitesEnabled](https://github.com/CDH-SC/WordPress/blob/master/exampleSitesEnabled) file, you can see that we are able to route site10.wordpress.cdhsc.org to the container listening on port 8010, which is defined to be container 10.

### How to install
`sudo apt install nginx`

![alt text](https://github.com/CDH-SC/WordPress/blob/master/README_images/nginxConfig.png "Nginx Config")

## **_Certbot_**
Used to generate ssl certification settings, located in the same sitesEnabled file that was previously referenced.
It uses the same certifcate for all website, located in /etc/letsencrypt/live/site1.wordpress.cdhsc.org/privkey.pem


### How to install
`sudo apt install certbot python3-certbot-nginx`
`certbot`

![alt text](https://github.com/CDH-SC/WordPress/blob/master/README_images/certbot.png "Certbot CLI")

## **_Docker_**
Docker daemon for running the docker containers

### How to install
- [Docs](https://docs.docker.com/install/)
- Just the commands

```
sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get remove --purge docker
sudo apt-get install docker-ce
```

### Make sure it's working
`sudo docker run hello-world`

![alt text](https://github.com/CDH-SC/WordPress/blob/master/README_images/dockerHelloWorld.png "Docker 'Hello World'")

## **_Docker-Compose_**
An orchestration tool for starting up the front end and back end containers (the script)

### How to install
- [Reference](https://docs.docker.com/compose/install/)
- Just the commands

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

![alt text](https://github.com/CDH-SC/WordPress/blob/master/README_images/dockerCompose.png "docker-compose starting")


# Testing and troubleshooting
---
`curl site1.wordpress.cdhsc.org`



# Credits
---
Credits to the people that worked together to get this tech stack working

- Robby Carff
- Joshua Nelson
- Zach Stump
