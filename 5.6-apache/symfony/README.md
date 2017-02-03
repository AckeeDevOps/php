# symfony

# Usage:

```
FROM ackee/php:5.6-apache-symfony
COPY . /var/www/

RUN rm -rf /var/www/html && \
    ln -s /var/www/web /var/www/html && \
    rm -rf /var/www/web/uploads && \
    ln -s /var/app-storage/uploads/ /var/www/web/uploads && \
    mkdir -p /var/www/app/cache/prod/ && \
    chown -R www-data:www-data /var/www/
```
