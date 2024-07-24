FROM php:8.2.10-fpm

# Copy configuration files
COPY ./conf/php.ini /usr/local/etc/php/

# Update package list and install necessary packages
RUN apt-get update && apt-get install -y \
    librabbitmq-dev \
    libpng-dev \
    libzip-dev \
    libxml2-dev \
    libpq-dev \
    libicu-dev

RUN apt-get install -y cron
RUN apt-get install -y nano

# Install PHP extensions
RUN docker-php-ext-install \
        intl \
        pdo \
        pdo_pgsql \
        xml \
        zip \
        gd \
        soap \
        bcmath \
        sockets

# Install additional PECL extensions
RUN pecl install http://pecl.php.net/get/amqp-2.1.1.tgz
RUN pecl install xdebug

# Enable installed extensions
RUN docker-php-ext-enable --ini-name 05-opcache.ini opcache amqp xdebug

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer

# Install PHP CS Fixer
RUN curl https://cs.symfony.com/download/php-cs-fixer-v2.phar --output /usr/local/bin/php-cs-fixer
RUN chmod +x /usr/local/bin/php-cs-fixer

# CRON
# COPY ./conf/cronjob-config /etc/cron.d/tfg-cronjob
# RUN chmod gu+s /var/run
# RUN chmod gu+s /run
# RUN chmod gu+s /usr/sbin/cron
# RUN crontab /etc/cron.d/tfg-cronjob

# CMD ["cron", "-f", "-L", "15", ">/dev/stdout", "2>/dev/stdout"]

# Create a user
RUN useradd -ms /sbin/nologin alexander

# Set the working directory
WORKDIR /var/www/html/backend
