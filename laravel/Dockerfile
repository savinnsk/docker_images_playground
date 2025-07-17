FROM php:8.4-cli    

WORKDIR /var/www

# INITIAL SETUP
RUN apt-get update && \
    apt install -y git && \
    apt-get install -y unzip && \
    apt-get install -y libzip-dev && \
    docker-php-ext-install zip

# COMPOSE INSTALL    
RUN  php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
     php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'.PHP_EOL; } else { echo 'Installer corrupt'.PHP_EOL; unlink('composer-setup.php'); exit(1); }" && \
     php composer-setup.php && \
     php -r "unlink('composer-setup.php');"

# LARAVEL INSTALL and CREATE PROJECT
RUN php composer.phar create-project --prefer-dist laravel/laravel laravel

ENTRYPOINT ["php","laravel/artisan", "serve"]

CMD ["--host=0.0.0.0"]





