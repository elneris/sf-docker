FROM httpd:2.4-alpine
MAINTAINER Elneris Dang <elneris.dang@omnilog.fr>

# Enable mpm_worker_module, proxy_fcgi_module, rewrite
COPY httpd-vhosts.conf /usr/local/apache2/conf/extra/httpd-vhosts.conf

# Use vhost config from https://symfony.com/doc/4.4/setup/web_server_configuration.html
COPY httpd.conf /usr/local/apache2/conf/httpd.conf
