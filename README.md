
# <b>Deploying Faveo Helpdesk on Docker</b>   <!-- omit in toc -->
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Docker_%28container_engine%29_logo.svg/440px-Docker_%28container_engine%29_logo.svg.png" alt="drawing" width="300"/>

## <b>Faveo Helpdesk Docker</b>

A pretty simplified Docker Compose workflow that sets up a network of containers for Faveo Helpdesk.

All the Faveo Helpdesk editions are supported except the community edition.

## <b>Usage</b>
___

To get started, make sure you have Docker and Docker-Compose installed on your system, and then clone the below Git-Hub repository with the below link.

[Git-Hub Repo Link](https://github.com/tamilselvan-lws/faveo-docker.git)

---
Next, navigate in your terminal to the directory you cloned this, and give the executable permissions to bash scripts.

### Apache 

```sh
chmod +x install-apache.sh
```
Usage:
```sh
./install-apache.sh -d|--domain <domain name> -e|--email <email> -l|--license <license> -o|--orderno <orderno>
```
Example: It should look something like this.
```sh
./install-apache.sh -d example.com -e dome@example.com -l F6LCG5XXXXXXXXX -o 3580XXXX
```
---
### NGINX

```sh
chmod +x install-nginx.sh
```
Usage:
```sh
./install-nginx.sh -d|--domain <domain name> -e|--email <email> -l|--license <license> -o|--orderno <orderno>
```

Example: It should look something like this.
```sh
./install-nginx.sh -d example.com -e dome@example.com -l F6LCG5XXXXXXXXX -o 3580XXXX
```

---
After the docker installation is completed you will be prompted with Database Credentials please copy and save them somewhere safe and a cronjob will be set to auto-renew SSL certificates from Letsencrypt

Visit https://yourdomainname complete the readiness probe, input the Database Details when prompted, and complete the installation.

There is one final step that needs to be done to complete the installation. You have to edit the .env file which is generated under the Faveo root directory after completing the installation in the browser. Open the terminal and navigate to the faveo-docker directory here you will find the directory "faveo" which is downloaded while running the script this directory contains all the Helpdesk codebase, inside it, you need to edit the ".env" file and add REDIS_HOST=faveo-redis. The "faveo-redis" is the DNS name of the Redis container. Finally, run the below command for changes to take effect.

#### Apache
```sh
docker-compose -f docker-compose-apache.yml down && docker-compose -f docker-compose-apache.yml up -d
```
  
#### NGINX
```sh
docker-compose -f docker-compose-nginx.yml down && docker-compose -f docker-compose-nginx.yml up -d
```

