# Use the official Ubuntu base image
FROM ubuntu:jammy-20230816
ENV TZ=Asia/Kolkata DEBIAN_FRONTEND=noninteractive

# Install Supervisor and update the package index

RUN apt update && apt -y install unzip wget git nano supervisor apt-utils ca-certificates curl gnupg lsb-release software-properties-common &&  rm -r /var/lib/apt/lists/*
RUN add-apt-repository ppa:ondrej/php
RUN apt install -y php8.1 libapache2-mod-php8.1 php8.1-mysql php8.1-cli php8.1-common php8.1-fpm php8.1-soap php8.1-gd php8.1-opcache  php8.1-mbstring php8.1-zip php8.1-bcmath php8.1-intl php8.1-xml php8.1-curl php8.1-imap php8.1-ldap php8.1-gmp php8.1-redis  &&  rm -r /var/lib/apt/lists/*
RUN apt-get clean
WORKDIR /var/www/html
COPY faveo-worker.conf /etc/supervisor/conf.d/faveo-worker.conf

CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]