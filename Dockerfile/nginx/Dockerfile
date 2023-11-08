# Use the official Ubuntu base image
FROM ubuntu:jammy-20230816
ENV TZ=Asia/Kolkata DEBIAN_FRONTEND=noninteractive

# Install Apache2 and update the package index
RUN apt-get update && apt-get install tzdata
RUN apt-get update && apt-get install software-properties-common -y
RUN add-apt-repository ppa:ondrej/php
RUN apt update && apt install -y nginx git wget curl unzip nano zip software-properties-common
RUN apt install -y php8.1 libapache2-mod-php8.1 php8.1-mysql php8.1-cli php8.1-common php8.1-fpm php8.1-soap php8.1-gd php8.1-opcache  php8.1-mbstring php8.1-zip php8.1-bcmath php8.1-intl php8.1-xml php8.1-curl php8.1-imap php8.1-ldap php8.1-gmp php8.1-redis  &&  rm -r /var/lib/apt/lists/*
COPY ioncube_loader_lin_8.1.so /usr/lib/php/20210902
RUN sed -i '2 a zend_extension = "/usr/lib/php/20210902/ioncube_loader_lin_8.1.so"' /etc/php/8.1/cli/php.ini
RUN sed -i '2 a zend_extension = "/usr/lib/php/20210902/ioncube_loader_lin_8.1.so"' /etc/php/8.1/fpm/php.ini
RUN apt update && apt-get -y install wkhtmltopdf
RUN apt-get clean
RUN sed -i -e 's/^file_uploads = .*/file_uploads = On/' \
           -e 's/^allow_url_fopen = .*/allow_url_fopen = On/' \
           -e 's/^short_open_tag = .*/short_open_tag = On/' \
           -e 's/^memory_limit = .*/memory_limit = 256M/' \
           -e 's/^cgi.fix_pathinfo = .*/cgi.fix_pathinfo = 0/' \
           -e 's/^upload_max_filesize = .*/upload_max_filesize = 100M/' \
           -e 's/^post_max_size = .*/post_max_size = 100M/' \
           -e 's/^max_execution_time = .*/max_execution_time = 360/' /etc/php/8.1/fpm/php.ini
RUN apt-get clean
WORKDIR /var/www/html

# Expose ports 80 and 443 for HTTP and HTTPS traffic
EXPOSE 80
EXPOSE 443

CMD service php8.1-fpm start && nginx -g "daemon off;"