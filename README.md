# docker-nginx-mysql-php
docker：nginx+mysql+php

#### 下载源码
~~~~
git clone https://github.com/selden1992/docker-nginx-mysql-php.git nmp
~~~~

## 修改配置

新建配置文件,其中variables.env.example是模板文件
~~~~
cp variables.env.example variables.env
~~~~

#### 修改mysql密码
~~~~
# MySQL settings
MYSQL_ROOT_PASSWORD=root密码
MYSQL_DATABASE=基础数据库
MYSQL_USER=基础用户
MYSQL_PASSWORD=Y基础用户密码
~~~~
#### nginx配置修改
修改文件域名
~~~~
nmp/config/nginx/sites-enable/default.conf
~~~~
如果需要多个域名配置，sites-enable新建目录即可，保证命名规则 
~~~~
*.conf
~~~~

# 启动使用

#### 进入目录构建image
~~~~
cd nmp
docker-compose build
~~~~
#### 启动下和下载其他image
~~~~
docker-compose up -d
~~~~

### 进入php容器

~~~~
docker exec -it php /bin/bash
~~~~
windows系统可能需要改bin才可已进入
~~~~
docker exec -it php /bin
~~~~


## 如果需要改php扩展
更改文件
~~~~
nmp/docker/php-app/Dockerfile
~~~~
新增gd扩展
~~~~
RUN docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install gd \
~~~~

改完后执行生效

~~~~
docker-compose stop
docker-compose build --no-cache php
docker-compose up -d
~~~~

### 重置容器

~~~~
docker-compose stop
docker-compose rm --force
~~~~