FROM varnish:latest

USER root

# Set Environment Variables
ENV DEBIAN_FRONTEND noninteractive

# Setting Configurations
ENV VARNISH_CONFIG  /etc/varnish/default.vcl
ENV CACHE_SIZE      512m
ENV VARNISHD_PARAMS -p default_ttl=3600 -p default_grace=3600 -p http_resp_hdr_len=700000 -p http_resp_size=1000000
ENV VARNISH_PORT    6081
ENV BACKEND_HOST    magento_app
ENV BACKEND_PORT    8003

COPY default.vcl /etc/varnish/default.vcl
COPY start.sh /etc/varnish/start.sh

RUN chmod +x /etc/varnish/start.sh

CMD ["/etc/varnish/start.sh"]

EXPOSE 8080 8003
