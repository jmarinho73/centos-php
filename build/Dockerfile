FROM centos:centos7.9.2009

# Instalar php8.1, apache e dependencias para composer
RUN yum -y install \
	https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
	&& yum -y install https://rpms.remirepo.net/enterprise/remi-release-7.rpm \
	&& yum -y install yum-utils && yum-config-manager --disable 'remi-php*' \
	&& yum-config-manager --enable remi-php81 && yum repolist && \
	yum -y install php php-{intl,mbstring,mysql,sqlite3,gd,xml,zip,cli} \
	httpd httpd-tools wget unzip

# Instalar composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php --install-dir=/usr/local/bin --filename=composer --version=2.4.3 \
  && composer

# Dependencias para wkhtmltox
RUN yum -y install \
  libXext libXrender openssl xorg-x11-fonts-75dpi xorg-x11-fonts-Type1

# Instalar wkhtmltox
RUN wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox-0.12.6-1.centos7.x86_64.rpm \
	 && rpm -i wkhtmltox-0.12.6-1.centos7.x86_64.rpm 

# Cambiar configuración de Apache
RUN sed -E -i -e '/<Directory "\/var\/www\/html">/,/<\/Directory>/s/AllowOverride None/AllowOverride All/' /etc/httpd/conf/httpd.conf
RUN sed -E -i -e 's/DirectoryIndex (.*)$/DirectoryIndex index.php \1/g' /etc/httpd/conf/httpd.conf

EXPOSE 80

# Arrancar Apache
CMD ["/usr/sbin/httpd","-D","FOREGROUND"] 
