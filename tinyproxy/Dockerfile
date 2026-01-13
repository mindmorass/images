FROM alpine:3.19

LABEL maintainer="mindmorass"
LABEL description="Tinyproxy - lightweight HTTP/HTTPS proxy"

RUN apk add --no-cache tinyproxy

# Create directories and set permissions
RUN mkdir -p /var/log/tinyproxy /var/run/tinyproxy && \
    chown -R nobody:nobody /var/log/tinyproxy /var/run/tinyproxy

# Copy default config
COPY tinyproxy.conf /etc/tinyproxy/tinyproxy.conf

EXPOSE 8888

USER nobody

CMD ["tinyproxy", "-d"]
