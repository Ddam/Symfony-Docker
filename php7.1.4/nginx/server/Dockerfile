FROM debian:jessie

# Install nginx server
RUN apt-get update && apt-get install -y \
    nginx

# Add configuration files
ADD etc/nginx/nginx.conf /etc/nginx/
ADD etc/nginx/sites-available/symfony.conf /etc/nginx/sites-available/
RUN ln -s /etc/nginx/sites-available/symfony.conf /etc/nginx/sites-enabled/symfony
RUN rm /etc/nginx/sites-enabled/default

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN usermod -u 1000 www-data

EXPOSE 80
EXPOSE 443

CMD ["nginx"]
