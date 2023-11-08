## Faveo Helpdesk Docker

A pretty simplified Docker Compose workflow set up a network of containers for the Faveo Helpdesk.
All the Faveo Helpdesk editions are supported.

```sh
git clone https://github.com/tamilselvan-lws/Docker-final.git
```
```sh
chmod +x install.sh
```

Usage:
```sh
 ./install.sh -d|--domain <domain name> -e|--email <email> -l|--license <license> -o|--orderno <orderno>
```
Example: It should look something like this.
```sh
 ./install.sh -d example.com -e dome@example.com -l F6LCG5XXXXXXXXX -o 3580XXXX
```

Note- You should have a Valid domain name pointing to your public IP. This domain name is used to obtain SSL certificates from Let's Encrypt CA, and the mail is used for the same purpose.


Visit https://yourdomainname complete the readiness probe, enter the Database information when prompted, and finish the installation.


```sh
docker compose down && docker compose up -d
```
	