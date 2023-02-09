FROM alpine
RUN apk --update --no-cache add build-base \
        openssl-dev \
        pcre-dev \
        zlib-dev \
        wget
RUN mkdir -p /tmp/src && \
    cd /tmp/src && \
    wget http://nginx.org/download/nginx-1.20.2.tar.gz && \
    tar zxf nginx-1.20.2.tar.gz && \
    cd nginx-1.20.2 && \
    ./configure --sbin-path=/usr/bin/nginx \
        --conf-path=/etc/nginx/nginx.conf \
        --pid-path=/var/run/nginx.pid \
        --error-log-path=/var/log/nginx/error.log \
        --http-log-path=/var/log/nginx/access.log \
        --with-pcre \
        --with-http_ssl_module && \
    make && \
    make install && \
    rm -rf /tmp/src && \
    echo "Hello, World!" > /usr/local/nginx/html/index.html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]