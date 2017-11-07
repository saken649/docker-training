FROM centos:latest

RUN yum -y update \
    && rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
    && rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm \
    && yum -y install \
        httpd \
        postfix \
        mod_php71w \
        php71w \
        php71w-cli \
        php71w-common \
        php71w-devel \
        php71w-fpm \
        php71w-gd \
        php71w-mbstring \
        php71w-mysql \
        php71w-pdo \
        php71w-pear \
        php71w-xml \
        php71w-pecl-xdebug

COPY ./conf/ /tmp/conf/

RUN mv /etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf.orig \
    && mv /tmp/conf/httpd.conf /etc/httpd/conf/httpd.conf \
    && mv /tmp/conf/xdebug.ini /etc/php.d/xdebug.ini \
    && systemctl enable httpd.service \
    && systemctl enable postfix