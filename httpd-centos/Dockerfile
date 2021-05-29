FROM centos
RUN yum install -y httpd
WORKDIR /var/www/html
COPY sitio .
ENV contenido prueba
RUN echo "$contenido" > /var/www/html/prueba.html
CMD apachectl -DFOREGROUND