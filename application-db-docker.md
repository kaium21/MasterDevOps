version: '3'
services:
  
  #PHP Service
  app:
    build:
      context: .
      dockerfile: Dockerfile
    image: digitalocean.com/php
    container_name: app
    restart: unless-stopped
    tty: true
    environment:
      SERVICE_NAME: app
      SERVICE_TAGS: dev
    working_dir: /var/www
    volumes:
      - ./:/var/www
      - ./php/local.ini:/usr/local/etc/php/conf.d/local.ini
    networks:
      - app-network

  #Nginx Service
  webserver:
    image: nginx:alpine
    container_name: webserver
    restart: unless-stopped
    tty: true
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./:/var/www
      - ./nginx/conf.d/:/etc/nginx/conf.d/
    networks:
      - app-network

  #MySQL Service
  db:
    image: mysql:5.7.22
    container_name: db
    restart: unless-stopped
    tty: true
    ports:
      - "3306:3306"
    environment:
      MYSQL_DATABASE: laravel
      MYSQL_ROOT_PASSWORD: root@123
      SERVICE_TAGS: dev
      SERVICE_NAME: mysql
    volumes:
      - dbdata:/var/lib/mysql/
      - ./mysql/my.cnf:/etc/mysql/my.cnf
    networks:
      - app-network

#Docker Networks
networks:
  app-network:
    driver: bridge
#Volumes
volumes:
  dbdata:
    driver: local


validating /root/laravel-app/docker-compose.yml:services.db.volumes.0 type is required

docker-compose up -d
parsing /root/laravel-app/docker-compose.yml:yaml:line 39: did not find expected key

bash: 276: command not found
bash: 0c2RR0: command not found
bash: 276: command not found
bash: 0c2RR0: command not found
bash: 276: command not found
bash: 0c2RR0: command not found
bash: 276: command not found
bash: 0c4RR0: command not found
bash: 276: command not found
bash: 0c2RR0: command not found
bash: 2: command not found
[node1] (local) root@192.168.0.28 ~/laravel-app
$ ^C
[node1] (local) root@192.168.0.28 ~/laravel-app
$ 
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi docker-compose.yml[node1] (local) root@192.168.0.28 ~/laravel-app
$ cat docker-compose.yml
version: '3'
services:
  
  #PHP Service
  app:
    build:
      context: .
      dockerfile: Dockerfile
    image: digitalocean.com/php
    container_name: app
    restart: unless-stopped
    tty: true
    environment:
      SERVICE_NAME: app
      SERVICE_TAGS: dev
    working_dir: /var/www
    volumes:
    - ./:/var/www
    - ./php/local.ini:/usr/local/etc/php/conf.d/local.ini
    networks:
      - app-network

  #Nginx Service
  webserver:
    image: nginx:alpine
    container_name: webserver
    restart: unless-stopped
    tty: true
    ports:
      - "80:80"
      - "443:443"
    volumes:
    - ./:/var/www
    - ./nginx/conf.d/:/etc/nginx/conf.d/
    networks:
      - app-network

  #MySQL Service
  db:
    image: mysql:5.7.22
    container_name: db
    restart: unless-stopped
    tty: true
    ports:
      - "3306:3306"
    environment:
      MYSQL_DATABASE: laravel
      MYSQL_ROOT_PASSWORD: root@123
      SERVICE_TAGS: dev
      SERVICE_NAME: mysql
    volumes:
    - type: volume
    source: dbdata
    target: /var/lib/mysql
    - ./mysql/my.cnf:/etc/mysql/my.cnf
    networks:
      - app-network

#Docker Networks
networks:
  app-network:
    driver: bridge
#Volumes
volumes:
  dbdata:
    driver: local
	
	
bash: RUN: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: php: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: COPY: command not found
bash: COPY: command not found
bash: USER: command not found
bash: EXPOSE: command not found
bash: CMD: command not found
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi ~/laravel-app/Dockerfile[node1] (local) root@192.168.0.28 ~/laravel-app$ vi dock
docker-comple       docker-compose.yml  
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi docker-comp
docker-comple       docker-compose.yml  
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi docker-compose.yml 
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi ~/laravel-app/Dockerfile
[node1] (local) root@192.168.0.28 ~/laravel-app
$ dock
docker                 docker-init            docker-scout           
docker-compose         docker-prompt          dockerd                
docker-entrypoint.sh   docker-proxy           dockerd-entrypoint.sh  
[node1] (local) root@192.168.0.28 ~/laravel-app
$ docker-compose up -d
[+] Running 1/1
 ! app Warning                                                                                        1.0s 
[+] Building 170.4s (11/17)                                                                 docker:default
 => [app internal] load .dockerignore                                                                 0.0s
 => => transferring context: 2B                                                                       0.0s
 => [app internal] load build definition from Dockerfile                                              0.0s
 => => transferring dockerfile: 1.28kB                                                                0.0s
 => [app internal] load metadata for docker.io/library/php:7.4-fpm                                    0.2s
 => [app  1/13] FROM docker.io/library/php:7.4-fpm@sha256:3ac7c8c74b2b047c7cb273469d74fc0d59b857aa44  0.0s
 => [app internal] load build context                                                                 2.0s
 => => transferring context: 725.35kB                                                                 1.9s
 => CACHED [app  2/13] COPY composer.lock composer.json /var/www/                                     0.0s
 => CACHED [app  3/13] WORKDIR /var/www                                                               0.0s
 => [app  4/13] RUN apt-get update && apt-get install -y     build-essential     libpng-dev     lib  24.0s
 => [app  5/13] RUN apt-get clean && rm -rf /var/lib/apt/lists/*                                      1.1s
 => [app  6/13] RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl                        132.9s
 => ERROR [app  7/13] RUN docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ -  10.2s
------
 > [app  7/13] RUN docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/:
7.964 Configuring for:
7.964 PHP Api Version:         20190902
7.964 Zend Module Api No:      20190902
7.964 Zend Extension Api No:   320190902
10.03 configure: error: unrecognized options: --with-gd, --with-freetype-dir, --with-jpeg-dir, --with-png-dir
------
WARN[0001] buildx: failed to read current commit information with git rev-parse --is-inside-work-tree 
failed to solve: process "/bin/sh -c docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/" did not complete successfully: exit code: 1



lete successfully: exit code: 1
[node1] (local) root@192.168.0.28 ~/laravel-app
$ 
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi FROM php:7.4-fpm

# Copy composer.lock and composer.json
COPY composer.lock composer.json /var/www/

# Set working directory
WORKDIR /var/www

# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
CMD ["php-fpm"]000 and start php-fpm serverssionsphp -- --install-dir=/usr/local/bin --filename=composer/ -
2 files to edit
bash: COPY: command not found
bash: WORKDIR: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: php: command not found
bash: RUN: command not found
bash: RUN: command not found
bash: COPY: command not found
bash: COPY: command not found
bash: USER: command not found
bash: EXPOSE: command not found
bash: CMD: command not found
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi ~/laravel-app/Dockerfile[node1] (local) root@192.168.0.28 ~/laravel-app$ vi dock
docker-comple       docker-compose.yml  
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi docker-comp
docker-comple       docker-compose.yml  
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi docker-compose.yml 
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi ~/laravel-app/Dockerfile
[node1] (local) root@192.168.0.28 ~/laravel-app
$ dock
docker                 docker-init            docker-scout           
docker-compose         docker-prompt          dockerd                
docker-entrypoint.sh   docker-proxy           dockerd-entrypoint.sh  
[node1] (local) root@192.168.0.28 ~/laravel-app
$ docker-compose up -d
[+] Running 1/1
 ! app Warning                                                                                        1.0s 
[+] Building 170.4s (11/17)                                                                 docker:default
 => [app internal] load .dockerignore                                                                 0.0s
 => => transferring context: 2B                                                                       0.0s
 => [app internal] load build definition from Dockerfile                                              0.0s
 => => transferring dockerfile: 1.28kB                                                                0.0s
 => [app internal] load metadata for docker.io/library/php:7.4-fpm                                    0.2s
 => [app  1/13] FROM docker.io/library/php:7.4-fpm@sha256:3ac7c8c74b2b047c7cb273469d74fc0d59b857aa44  0.0s
 => [app internal] load build context                                                                 2.0s
 => => transferring context: 725.35kB                                                                 1.9s
 => CACHED [app  2/13] COPY composer.lock composer.json /var/www/                                     0.0s
 => CACHED [app  3/13] WORKDIR /var/www                                                               0.0s
 => [app  4/13] RUN apt-get update && apt-get install -y     build-essential     libpng-dev     lib  24.0s
 => [app  5/13] RUN apt-get clean && rm -rf /var/lib/apt/lists/*                                      1.1s
 => [app  6/13] RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl                        132.9s
 => ERROR [app  7/13] RUN docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ -  10.2s
------
 > [app  7/13] RUN docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/:
7.964 Configuring for:
7.964 PHP Api Version:         20190902
7.964 Zend Module Api No:      20190902
7.964 Zend Extension Api No:   320190902
10.03 configure: error: unrecognized options: --with-gd, --with-freetype-dir, --with-jpeg-dir, --with-png-dir
------
WARN[0001] buildx: failed to read current commit information with git rev-parse --is-inside-work-tree 
failed to solve: process "/bin/sh -c docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/" did not complete successfully: exit code: 1
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi ~/laravel-app/Dockerfile
[node1] (local) root@192.168.0.28 ~/laravel-app
existing docker file for php configuration
cat ~/laravel-app/Dockerfile
FROM php:7.4-fpm

# Copy composer.lock and composer.json
COPY composer.lock composer.json /var/www/

# Set working directory
WORKDIR /var/www

# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    libjpeg62-turbo-dev \
    libonig-dev \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl \
    libzip-dev

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install extensions
RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl
RUN docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/
RUN docker-php-ext-install gd

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Add user for laravel application
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

# Copy existing application directory contents
COPY . /var/www

# Copy existing application directory permissions
COPY --chown=www:www . /var/www

# Change current user to www
USER www

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]
