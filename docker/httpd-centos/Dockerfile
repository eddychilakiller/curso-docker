FROM centos
LABEL version=1.0
LABEL uso="curso de docker"

RUN yum install -y httpd
WORKDIR /var/www/html
COPY sitio .
ENV contenido prueba
RUN echo "$contenido" > /var/www/html/prueba.html
EXPOSE 8080
CMD apachectl -DFOREGROUND