FROM ubuntu:focal

RUN apt update && apt upgrade -y
RUN apt install curl keepalived haproxy -y

COPY check_apiserver.sh /etc/keepalived/check_apiserver.sh
RUN chmod +x /etc/keepalived/check_apiserver.sh
COPY keepalived.conf /etc/keepalived/keepalived.conf
RUN systemctl enable --now keepalived

COPY haproxy.cfg /etc/haproxy/haproxy.cfg
RUN systemctl enable haproxy && sudo systemctl restart haproxy