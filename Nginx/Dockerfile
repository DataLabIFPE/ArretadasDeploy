FROM ubuntu

RUN apt-get update
RUN apt-get install nginx -y

WORKDIR  /app-bi
COPY ./BI-Arretadas/ .
RUN cd ..
COPY ./server/arretadasAPI /etc/nginx/sites-available
COPY ./server/arretadasBI /etc/nginx/sites-available

RUN rm /etc/nginx/sites-enabled/default
RUN rm /etc/nginx/sites-available/default

RUN ln -sfn /etc/nginx/sites-available/arretadasAPI /etc/nginx/sites-enabled/
RUN ln -sfn /etc/nginx/sites-available/arretadasBI /etc/nginx/sites-enabled/

RUN service nginx reload
RUN service nginx restart

EXPOSE 80

ENTRYPOINT ["/usr/sbin/nginx"]
CMD ["-g","daemon off;"]