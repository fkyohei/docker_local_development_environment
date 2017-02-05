FROM centos:7

# Install & Add repo
RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

# Install Apache
RUN yum -y install httpd

# Install PHP7
RUN yum -y install —enablerepo=remi-php70 php php-mcrypt php-cli php-common php-devel php-gd php-mbstring php-mysqlnd php-opcache php-pdo php-pear php-xml

# Install openssl
RUN yum -y install mod_ssl

# Clear yum cache
RUN yum clean all

# PORT
EXPOSE 80
EXPOSE 443

# SET httpd.conf
ADD httpd.conf /etc/httpd/conf/httpd.conf

# SET php.ini
ADD php.ini /etc/php.ini

# SET ssl.conf
ADD ssl.conf /etc/httpd/conf.d/ssl.conf

# SET SSL KEY
ADD localhost.key /etc/pki/tls/private/localhost.key
ADD localhost.crt /etc/pki/tls/certs/localhost.crt

# EXEC FOREGROUND
CMD /usr/sbin/httpd -DFOREGROUND
