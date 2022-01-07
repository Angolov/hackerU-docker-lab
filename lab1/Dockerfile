FROM debian
MAINTAINER angolov

RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y nginx \
    && apt-get clean \
    && rm -rf /var/www \
    && mkdir -p /var/www/company.com /var/www/company.com/img \
    && useradd anton \
    && groupadd golovatyy \
    && usermod -a -G golovatyy anton \
    && chmod -R 754 /var/www/company.com \
    && chown -R anton:golovatyy /var/www/company.com \
    && sed -i 's#/var/www/html#/var/www/company.com#g' /etc/nginx/sites-enabled/default \
    && sed -i 's#user\s*\S*;#user  anton;#g' /etc/nginx/nginx.conf

COPY index.html /var/www/company.com/
COPY empire.jpg /var/www/company.com/img/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
