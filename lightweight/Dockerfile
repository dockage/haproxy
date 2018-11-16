FROM alpine:3.8

LABEL MAINTAINER="khashayar.danesh@gmail.com"

RUN apk add --update --no-cache haproxy \
        ca-certificates \
        zlib-dev

COPY docker-entrypoint.sh /

RUN chmod +x docker-entrypoint.sh

ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["haproxy", "-f", "/usr/local/etc/haproxy/haproxy.cfg"]