FROM centos:7
MAINTAINER Centos7

RUN yum -y update

# 外部リポジトリ（EPEL, Remi）を追加
RUN yum -y install epel-release
RUN yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm

# apache その他 phpパッケージを導入
RUN yum -y install httpd
RUN yum -y install --enablerepo=remi,remi-php72 php php-cli php-common php-devel php-fpm php-gd php-mbstring php-mysqlnd php-pdo php-pear php-pecl-apcu php-soap php-xml php-xmlrpc php-pgsql
RUN yum -y install zip unzip nodejs
RUN yum -y install make gcc glibc-devel zlib-devel openssl-devel php-devel
RUN yum -y install wget
RUN npm cache clean -f
RUN npm install -g n
RUN n stable

# composerのインストール
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

CMD ["/usr/sbin/httpd","-D","FOREGROUND"]

# WORKDIR /var/www/html