FROM alpine:3.3
MAINTAINER SSquared

RUN apk add --update unzip

RUN mkdir -p /var/consul/data
ADD https://releases.hashicorp.com/consul/0.6.3/consul_0.6.3_linux_amd64.zip /tmp/consul.zip
RUN unzip /tmp/consul.zip -d /var/consul

COPY ./consul-entrypoint.sh /var/consul/consul-entrypoint.sh
RUN chmod 755 /var/consul/consul-entrypoint.sh

ENTRYPOINT ["/var/consul/consul-entrypoint.sh"]

CMD ["/var/consul/consul", "agent", "-server", "-config-file=/var/consul/consul.json"]
