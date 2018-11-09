FROM php:7.2-fpm

# Install libraries
RUN apt-get update && apt-get install -y --no-install-recommends apt-utils\
    git \
    zip unzip \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    zlib1g-dev \
    nano \
    && docker-php-ext-install -j$(nproc) iconv zip mysqli pdo pdo_mysql \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd


# Install composer
RUN curl -sSk https://getcomposer.org/installer | php -- --disable-tls --install-dir=/usr/local/bin --filename=composer

# Install node
#RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -
#RUN apt-get install -y nodejs -t testing npm
#RUN node -v
#RUN npm -v


# Create the project directory
# WORKDIR /var/www/laravel
# Copy the whole project to your workdir
# COPY . .
# COPY . ./laravel-scaffold
# RUN composer install
# EXPOSE 9000

### OPTIONAL
# Install xdebug
# RUN pecl install xdebug && \
#     docker-php-ext-enable xdebug

# Install bashit
# RUN git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it && ~/.bash_it/install.sh \
#     && mkdir -p ~/.bash_it/plugins/enabled/ \
#     && ln -s ~/.bash_it/plugins/available/history.plugin.bash ~/.bash_it/plugins/enabled/250---history.plugin.bash \
#     && sed -i 's/bobby/sexy/' ~/.bashrc
