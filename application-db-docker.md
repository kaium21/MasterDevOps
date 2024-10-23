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














node1] (local) root@192.168.0.28 ~/laravel-app
$ php artisan config:clear
bash: php: command not found
[node1] (local) root@192.168.0.28 ~/laravel-app
$ php artisan config:clear
bash: php: command not found
[node1] (local) root@192.168.0.28 ~/laravel-app
$ docker-compose exec app php artisan config:clear

   INFO  Configuration cache cleared successfully.  

[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi dock
docker-comple       docker-compose.yml  
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi docker-compose.yml 
[node1] (local) root@192.168.0.28 ~/laravel-app
$  mysql -h 127.0.0.1 -P 3306 -u root
bash: mysql: command not found
[node1] (local) root@192.168.0.28 ~/laravel-app
$ docker-compose exec app mysql -h 127.0.0.1 -P 3306 -u root
OCI runtime exec failed: exec failed: unable to start container process: exec: "mysql": executable file not found in $PATH: unknown
[node1] (local) root@192.168.0.28 ~/laravel-app
$ #docker-compose exec app mysql -h 127.0.0.1 -P 3306 -u root
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi .env
[node1] (local) root@192.168.0.28 ~/laravel-app
$ #docker-compose exec db mysql -h 127.0.0.1 -P 3306 -u root
[node1] (local) root@192.168.0.28 ~/laravel-app
$ docker-compose exec db mysql -h 127.0.0.1 -P 3306 -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
[node1] (local) root@192.168.0.28 ~/laravel-app
$ docker-compose exec db mysql -h 127.0.0.1 -P 3306 -u root -p 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 5.7.22-log MySQL Community Server (GPL)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SELECT user, host FROM mysql.user;
+---------------+-----------+
| user          | host      |
+---------------+-----------+
| root          | %         |
| mysql.session | localhost |
| mysql.sys     | localhost |
| root          | localhost |
+---------------+-----------+
4 rows in set (0.01 sec)

mysql> exit
Bye
[node1] (local) root@192.168.0.28 ~/laravel-app
$ vi .env
[node1] (local) root@192.168.0.28 ~/laravel-app
$ docker-compose run --service-ports db
[+] Building 0.0s (0/0)                                                                     docker:default
[+] Building 0.0s (0/0)                                                                     docker:default
ERRO[0000] error waiting for container:                 
Error response from daemon: driver failed programming external connectivity on endpoint laravel-app-db-run-7d42cc346f52 (e7aaad647b7ed1260157733cda575def3698dc22a835eba18dad08a1d908ecd9): Bind for 0.0.0.0:3306 failed: port is already allocated
[node1] (local) root@192.168.0.28 ~/laravel-app
$ docker-compose down
[+] Running 4/4
 ✔ Container db                     Removed                                                           1.9s 
 ✔ Container app                    Removed                                                           0.5s 
 ✔ Container webserver              Removed                                                           0.5s 
 ✔ Network laravel-app_app-network  Removed                                                           0.1s 
[node1] (local) root@192.168.0.28 ~/laravel-app
$ docker-compose run --service-ports db
[+] Building 0.0s (0/0)                                                                     docker:default
[+] Creating 1/0
 ✔ Network laravel-app_app-network  Created                                                           0.1s 
[+] Building 0.0s (0/0)                                                                     docker:default
2024-05-30T17:45:31.551589Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2024-05-30T17:45:31.554322Z 0 [Note] mysqld (mysqld 5.7.22-log) starting as process 1 ...
2024-05-30T17:45:31.558923Z 0 [Note] InnoDB: PUNCH HOLE support available
2024-05-30T17:45:31.558972Z 0 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2024-05-30T17:45:31.558979Z 0 [Note] InnoDB: Uses event mutexes
2024-05-30T17:45:31.558985Z 0 [Note] InnoDB: GCC builtin __atomic_thread_fence() is used for memory barrier
2024-05-30T17:45:31.558990Z 0 [Note] InnoDB: Compressed tables use zlib 1.2.3
2024-05-30T17:45:31.559007Z 0 [Note] InnoDB: Using Linux native AIO
2024-05-30T17:45:31.559548Z 0 [Note] InnoDB: Number of pools: 1
2024-05-30T17:45:31.560085Z 0 [Note] InnoDB: Using CPU crc32 instructions
2024-05-30T17:45:31.564434Z 0 [Note] InnoDB: Initializing buffer pool, total size = 128M, instances = 1, chunk size = 128M
2024-05-30T17:45:31.580731Z 0 [Note] InnoDB: Completed initialization of buffer pool
2024-05-30T17:45:31.585570Z 0 [Note] InnoDB: If the mysqld execution user is authorized, page cleaner thread priority can be changed. See the man page of setpriority().
2024-05-30T17:45:31.598534Z 0 [Note] InnoDB: Highest supported file format is Barracuda.
2024-05-30T17:45:31.610925Z 0 [Note] InnoDB: Creating shared tablespace for temporary tables
2024-05-30T17:45:31.611079Z 0 [Note] InnoDB: Setting file './ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
2024-05-30T17:45:31.633023Z 0 [Note] InnoDB: File './ibtmp1' size is now 12 MB.
2024-05-30T17:45:31.635164Z 0 [Note] InnoDB: 96 redo rollback segment(s) found. 96 redo rollback segment(s) are active.
2024-05-30T17:45:31.635198Z 0 [Note] InnoDB: 32 non-redo rollback segment(s) are active.
2024-05-30T17:45:31.636367Z 0 [Note] InnoDB: 5.7.22 started; log sequence number 12359316
2024-05-30T17:45:31.636685Z 0 [Note] InnoDB: Loading buffer pool(s) from /var/lib/mysql/ib_buffer_pool
2024-05-30T17:45:31.636987Z 0 [Note] Plugin 'FEDERATED' is disabled.
2024-05-30T17:45:31.641387Z 0 [Note] InnoDB: Buffer pool(s) load completed at 240530 17:45:31
2024-05-30T17:45:31.645484Z 0 [Note] Found ca.pem, server-cert.pem and server-key.pem in data directory. Trying to enable SSL support using them.
2024-05-30T17:45:31.645764Z 0 [Warning] CA certificate ca.pem is self signed.
2024-05-30T17:45:31.648589Z 0 [Note] Server hostname (bind-address): '*'; port: 3306
2024-05-30T17:45:31.649149Z 0 [Note] IPv6 is available.
2024-05-30T17:45:31.649206Z 0 [Note]   - '::' resolves to '::';
2024-05-30T17:45:31.649250Z 0 [Note] Server socket created on IP: '::'.
2024-05-30T17:45:31.672320Z 0 [Note] Event Scheduler: Loaded 0 events
2024-05-30T17:45:31.672772Z 0 [Note] mysqld: ready for connections.
Version: '5.7.22-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)

2024-05-30T17:45:54.924508Z 2 [Warning] IP address '172.18.0.1' could not be resolved: Name or service not known
                                                                              



























--- docker-compose.yml

version: '3'
services:

  # PHP Service
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

  # Nginx Service
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

  # MySQL Service
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

# Docker Networks
networks:
  app-network:
    driver: bridge

# Volumes
volumes:
  dbdata:
    driver: local


~/laravel-app/Dockerfile

----------------------------------------------------

FROM php:8.3-fpm

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

# Configure and install gd extension
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
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

---------------------------------------------------------


CREATE USER 'laraveluser'@'%' IDENTIFIED BY 'your_password';


ALTER USER 'laraveluser'@'%' IDENTIFIED BY 'laraveluser@123';
