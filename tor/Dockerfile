FROM alpine:3.15

RUN echo http://dl-cdn.alpinelinux.org/alpine/edge/testing >> /etc/apk/repositories && \
    apk update --no-cache && apk add --no-cache tor obfs4proxy curl && \
    chmod 700 /var/lib/tor

EXPOSE 9050

HEALTHCHECK --interval=60s --timeout=30s --start-period=20s --retries=3 \
    CMD curl -s --socks5 127.0.0.1:9050 'https://check.torproject.org/' | grep -qm1 Congratulations

CMD ["tor"]
