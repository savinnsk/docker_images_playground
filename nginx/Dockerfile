# old
#FROM nginx:latest
#COPY html/ /usr/share/nginx/html
#ENTRYPOINT ["/docker-entrypoint.sh"]
#CMD ["nginx","-g","daemon off;"]


FROM nginx:1.15.0-alpine

RUN rm /etc/nginx/conf.d/default.conf

COPY nginx.conf  /etc/nginx/conf.d

RUN mkdir /var/www/html -p && touch /var/www/html/index.php

CMD ["nginx","-g","daemon off;"]