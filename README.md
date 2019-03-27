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
| [Google Cloud Console](https://cloud.google.com/)     | Interface for booting up VMs        | Hosted by Google  |
| [Google Cloud DNS](https://cloud.google.com/)         | Interface for configuring DNS       | Hosted by Google  |
| [Nginx](https://www.nginx.com)                        | Proxy on VM                         | Installed on VM   |
| [Certbot](https://certbot.eff.org/)                   | secure connections to containers    | Installed on VM   |
| [Docker CE](https://docs.docker.com/v17.12/install/)  | daemon for running containers       | Installed on VM   |
| [Docker-compose](https://docs.docker.com/compose/)    | orchestraion of multiple Containers | Installed on VM   |


# Configurations
---

## **_Google Cloud Console_**

## **_Google Cloud DNS_**

## **_Nginx_**
Used on the machine to manage connections. Referencing the the [exampleSitesEnabled](https://github.com/CDH-SC/WordPress/blob/master/exampleSitesEnabled) file, you can see that we are able to route site10.wordpress.cdhsc.org to the container listening on port 8010, which is defined to be container 10.

How to install

Images of the file and its location

## **_Certbot_**
Used to generate ssl certification settings, located in the same sitesEnabled file that was previously referenced.
It uses the same certifcate for all website, located in /etc/letsencrypt/live/site1.wordpress.cdhsc.org/privkey.pem


How to install

Images of the file and its location

## **_Docker_**
Docker daemon for running the docker containers

How to install

commands to see the version/testing if it was correctly installed

## **_Docker-Compose_**
An orchestraion tool for starting up the front end and back end containers (the script)

How to install

Images of the file and its location
  
  
# Testing and troubleshooting
---
Testing the configure



# Credits
---
Credits to the people that worked together to get this tech stack working
