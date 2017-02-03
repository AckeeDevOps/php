# php
PHP base images for running (not building!!) nette, symfony, silex php apps

# Usage:

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
