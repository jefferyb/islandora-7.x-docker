# To build, do:
#   $ docker build -t islandora-enterprise-all-in-one --pull .
#
# To run, do:
#   $ docker run -d --name islandora-enterprise-all-in-one -p 80:80 -p 8080:8080 islandora-enterprise-all-in-one

FROM jefferyb/ansible:trusty
MAINTAINER Jeffery Bagirimvano <jefferyb@uark.edu>

RUN \
    git clone https://github.com/jefferyb/islandora-7.x-enterprise-ansible.git /root/islandora-7.x-Enterprise && \
    cd /root/islandora-7.x-Enterprise && \
    ansible-playbook install-islandora-7.x-enterprise.yaml && \
    service apache2 stop && \
    pkill java && \
    service mysql stop && \
    rm -fv /var/log/tomcat7/*

EXPOSE 80 3306 8080

CMD \
    service mysql restart && \
    service tomcat7 start && \
    service apache2 restart && \
    drush --root=/var/www/html -y updatedb && \
    drush --root=/var/www/html -y core-cron && \
    tail -f /var/log/tomcat7/catalina.out \
         -f /var/log/apache2/*.log \
         -f /usr/local/fedora/server/logs/*.log
