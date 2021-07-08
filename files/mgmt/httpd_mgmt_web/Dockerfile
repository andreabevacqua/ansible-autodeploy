FROM httpd
LABEL maintainer="Eusebiu Cristea <e.cristea@almaviva.it>"
COPY landing-page htdocs/mgmt
COPY derekeder.csv-to-html-table htdocs/mgmt/reports
RUN  rm -f htdocs/mgmt/reports/index.html
COPY lista_log_applicazioni.html htdocs/mgmt/reports/
COPY lista_applicazioni.html htdocs/mgmt/reports/
COPY lista_applicazioni_interne.html htdocs/mgmt/reports/
COPY lista_virtualhost.html htdocs/mgmt/reports/
COPY lista_connessioni_db.html htdocs/mgmt/reports/
COPY lista_storage_san.html htdocs/mgmt/reports/
COPY mgmt.conf conf/extra/
COPY server.crt server.key conf/
COPY gitlab.crt gitlab.key conf/
RUN  /bin/echo "Include conf/extra/mgmt.conf" >> conf/httpd.conf
RUN  sed -i \
        -e 's/^#\(Include .*httpd-ssl.conf\)/\1/' \
        -e 's/^#\(LoadModule .*mod_ssl.so\)/\1/' \
        -e 's/^#\(LoadModule .*mod_socache_shmcb.so\)/\1/' \
        conf/httpd.conf
