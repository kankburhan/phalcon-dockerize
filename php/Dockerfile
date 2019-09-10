FROM phpdockerio/php72-fpm:latest
WORKDIR "/application"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install selected extensions and other stuff
RUN apt-get update \
&& apt-get -y --no-install-recommends install  php7.2-mysql php-redis php-xdebug php7.2-bcmath php7.2-bz2 php7.2-gd php7.2-intl php-ssh2 php7.2-xsl php-yaml \
&& apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install phalcon
RUN curl -s https://packagecloud.io/install/repositories/phalcon/stable/script.deb.sh | bash \
&& apt-get install -y php7.2-phalcon=3.4.2-2+php7.2 \
&& apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install git
RUN apt-get update \
&& apt-get -y install git \
&& apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

ENV DEVTOOLS_VERSION=3.4.1
RUN curl -LO https://github.com/phalcon/phalcon-devtools/archive/v${DEVTOOLS_VERSION}.tar.gz \
    && tar xzf v${DEVTOOLS_VERSION}.tar.gz \
    && mv phalcon-devtools-${DEVTOOLS_VERSION} /usr/local/phalcon-devtools \
    && ln -s /usr/local/phalcon-devtools/phalcon.php /usr/local/bin/phalcon \
    && rm -f v${DEVTOOLS_VERSION}.tar.gz

# composer
ENV COMPOSER_VERSION=1.8.3
RUN curl -L https://getcomposer.org/installer -o composer-setup.php \
    && php composer-setup.php --version=${COMPOSER_VERSION} --install-dir=/usr/local/bin --filename=composer \
    && rm -f composer-setup.php


# Install Dependency
RUN apt install php7.2-gmp 