FROM php:7.4-fpm

# Dossier de travail
WORKDIR /var/www

# Installer les dépendences
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Get composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Ajouter user laravel
RUN useradd -G www-data,root -u 1000 -d /home/kim kim
RUN mkdir -p /home/kim/.composer && \
    chown -R kim:kim /home/kim

USER kim