# Use an official PHP image with Apache
FROM php:8.2-apache

# Set working directory
WORKDIR /var/www/html

# Install dependencies
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    zip \
    libzip-dev \
    unzip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo_mysql zip

# Enable Apache mod_rewrite
RUN a2enmod rewrite

# Copy the Laravel app code into the container
COPY . .

# Copy custom Apache configuration and Change Apache port from 80 to 8000
RUN cp /var/www/html/aconf/000-default.conf /etc/apache2/sites-available/000-default.conf
RUN sed -i 's/Listen 80/Listen 8000/' /etc/apache2/ports.conf 

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN composer install --no-dev --optimize-autoloader

# Set proper permissions
RUN chown -R www-data:www-data /var/www/html 
RUN chmod -R 777 /var/www/html

#migrate database schema
RUN php artisan migrate


# Expose port 80
EXPOSE 8000

# Start Apache service
CMD ["apache2-foreground"]

