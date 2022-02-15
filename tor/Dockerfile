FROM alpine:3.15

RUN echo http://dl-cdn.alpinelinux.org/alpine/edge/testing >> /etc/apk/repositories && \
    apk update --no-cache && apk add --no-cache tor obfs4proxy curl && \
    sed "1s/^/SocksPort 0.0.0.0:9050\n/" /etc/tor/torrc.sample > /etc/tor/torrc && \
    chown tor:root /var/lib/tor && \
    chmod 700 /var/lib/tor

EXPOSE 9050

HEALTHCHECK --interval=60s --timeout=15s --start-period=25s \
    CMD curl -s --socks5 127.0.0.1:9050 'https://check.torproject.org/' | grep -qm1 Congratulations

#VOLUME ["/var/lib/tor"]

#USER tor

CMD ["tor"]
