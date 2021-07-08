## Run Container
cd /opt/docker/httpd-gev-mgmt
git pull
docker build --rm -f "Dockerfile" -t httpd-mgmt .
docker rm -f httpd-mgmt-01
docker run -d --restart always --name httpd-mgmt-01 -p 443:443 --link awx_web:awx_web -v /var/lib/awx/projects/_28__ansible_gev/files/reports:/usr/local/apache2/htdocs/mgmt/reports/data --network awx_default httpd-mgmt

# + gitlab
docker run --detach --restart always --name httpd-mgmt-01 --publish 443:443 --link awx_web:awx_web --link gitlab:gitlab --volume /var/lib/awx/projects/_28__ansible_gev/files/reports:/usr/local/apache2/htdocs/mgmt/reports/data --network awx_default httpd-mgmt
