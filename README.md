# php
PHP base images for running (not building!!) nette, symfony, silex php apps

# Usage:
*  `/var/app-storage/` is a persistent volume
*  `/var/www/www/` is a new webspace root (via symlink)
*  `/var/www/html/upload` is a symlink to persistent volume's dir upload
```
FROM ackee/php:5.6-apache-silex
COPY . /var/www/
RUN chown -R www-data:www-data /var/www/ && \
    su -s /bin/bash www-data -c '\ 
       rm -rf /var/www/html/ && \
       ln -s /var/www/www/ /var/www/html && \
       rm -r /var/www/html/upload && \
       ln -s /var/app-storage/upload /var/www/html/upload && \
       ln -s ../log/ /var/www/www/log'
```       
