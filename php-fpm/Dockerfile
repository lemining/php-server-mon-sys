FROM raddiscentis/php-fpm:0.0.1
MAINTAINER Rex Addiscentis <raddiscentis@addiscent.com>

CMD ["/sbin/my_init"]

RUN mkdir -p /var/www/public

COPY ./phpinfo.php /var/www/public/phpinfo.php

COPY ./phpservermon-3.1.1.tar.gz /
RUN tar -zxvf ./phpservermon-3.1.1.tar.gz -C /var/www/public/ --strip-components=2
RUN rm ./phpservermon-3.1.1.tar.gz

COPY ./psm_config.php /var/www/public/config.php

RUN chown -R www-data:www-data /var/www/public
RUN chmod -R 755 /var/www/public

# RUN mkdir -p /etc/service/php-fpm
# ADD start.sh /etc/service/php-fpm/run
# RUN chmod +x /etc/service/php-fpm/run

COPY ./php-fpm.conf /etc/php5/fpm/php-fpm.conf
COPY ./www.conf /etc/php5/fpm/pool.d/www.conf
COPY ./php.ini /etc/php5/fpm/php.ini

COPY ./etc-cron.d-tab-for-phpfpm.txt /etc/cron.d/phpservermon
RUN chown root:root /etc/cron.d/phpservermon
RUN chmod 600 /etc/cron.d/phpservermon

EXPOSE 9000

VOLUME /var/www/public
