FROM centos:centos7

RUN mkdir -p /etc/nginx/conf.d/
VOLUME /etc/nginx/conf.d

COPY conf/gitlab.conf /etc/nginx/conf.d/gitlab.conf
COPY conf/jenkins.conf /etc/nginx/conf.d/jenkins.conf
COPY conf/ldapaccountmanager.conf /etc/nginx/conf.d/ldapaccountmanager.conf
COPY conf/nginx.conf /etc/nginx/nginx.conf

