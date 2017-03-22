FROM centos:7

# Initial setup
RUN yum update -y
RUN yum install -y epel-release wget which less gcc curl libcurl libcurl-devel gcc-c++ autoconf automake vim git
RUN wget http://rpms.remirepo.net/enterprise/remi-release-7.rpm && rpm -Uvh remi-release-7.rpm && yum-config-manager --enable remi-php70
RUN yum update -y && rm remi-release-7.rpm

# Setup oh-my-zsh
RUN yum install -y zsh && chsh -s /bin/zsh
RUN sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"

# Install PHP and extensions
RUN yum install -y \
php71 \
php71-php-bcmath \
php71-php-cli \
php71-php-common \
php71-php-dba \
php71-php-dbg \
php71-php-fpm \
php71-php-gd \
php71-php-intl \
php71-php-json \
php71-php-mbstring \
php71-php-mcrypt \
php71-php-odbc \
php71-php-opcache \
php71-php-pdo \
php71-php-pear \
php71-php-pgsql \
php71-php-phpiredis \
php71-php-pear \
php71-php-sqlsrv \
php71-php-xml \
php71-php-xmlrpc \
php71-php-pecl-xdebug \
php71-php-devel

# Use php.ini for DEV
RUN mv /etc/opt/remi/php71/php.ini /etc/opt/remi/php71/php.ini-production
RUN wget -O /etc/opt/remi/php71/php.ini https://raw.githubusercontent.com/php/php-src/PHP-7.1/php.ini-development

# Install composer
RUN mkdir -p /var/www/html && cd /var/www/html/
RUN ln -s /usr/bin/php71 /usr/bin/php
COPY composer-install.sh /var/www/html/
RUN chmod +x /var/www/html/composer-install.sh
RUN /var/www/html/composer-install.sh && \
rm /var/www/html/composer-install.sh && mv composer.phar /usr/bin/composer && \
composer self-update

# Install Node.js
RUN curl --silent --location https://rpm.nodesource.com/setup_6.x | bash -
RUN yum install -y nodejs