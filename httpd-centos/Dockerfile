FROM centos
RUN yum install -y httpd
CMD apachectl -DFOREGROUND
COPY sitio /var/www/html
ENV contenido prueba
RUN echo "$contenido" > /var/www/html/prueba.html
CMD apachectl -DFOREGROUND