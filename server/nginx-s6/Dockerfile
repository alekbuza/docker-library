ARG ALPINELINUX_S6_VERSION

FROM aleksandarbuza/alpinelinux-s6:${ALPINELINUX_S6_VERSION} as build

ARG NGINX_VERSION

WORKDIR /opt

RUN set -ex \
  && apk add --no-cache --virtual .build-deps \
    build-base \
    linux-headers \
    openssl-dev \
    pcre-dev \
    wget \
    zlib-dev \
  && apk add --no-cache \
    ca-certificates \
    pcre \
    zlib \
    tzdata \
    git \
  && wget https://nginx.org/download/nginx-$NGINX_VERSION.tar.gz \
  && tar xzf nginx-$NGINX_VERSION.tar.gz \
  && cd nginx-$NGINX_VERSION \
  && ./configure \
    --prefix=/etc/nginx \
    --sbin-path=/usr/sbin/nginx \
    --conf-path=/etc/nginx/nginx.conf \
    --error-log-path=/var/log/nginx/error.log \
    --http-log-path=/var/log/nginx/access.log \
    --pid-path=/var/run/nginx.pid \
    --lock-path=/var/run/nginx.lock \
    --http-client-body-temp-path=/var/cache/nginx/client_temp \
    --http-proxy-temp-path=/var/cache/nginx/proxy_temp \
    --http-fastcgi-temp-path=/var/cache/nginx/fastcgi_temp \
    --http-uwsgi-temp-path=/var/cache/nginx/uwsgi_temp \
    --http-scgi-temp-path=/var/cache/nginx/scgi_temp \
    --user=nginx \
    --group=nginx \
    --with-http_ssl_module \
    --with-http_realip_module \
    --with-http_addition_module \
    --with-http_sub_module \
    --with-http_dav_module \
    --with-http_flv_module \
    --with-http_mp4_module \
    --with-http_gunzip_module \
    --with-http_gzip_static_module \
    --with-http_random_index_module \
    --with-http_secure_link_module \
    --with-http_stub_status_module \
    --with-http_auth_request_module \
    --with-mail \
    --with-mail_ssl_module \
    --with-file-aio \
    --with-threads \
    --with-stream \
    --with-stream_ssl_module \
    --with-stream_realip_module \
    --with-http_slice_module \
    --with-http_v2_module \
  && make \
  && make install \
  && addgroup -S nginx \
  && adduser -D -S -h /var/cache/nginx -s /sbin/nologin -G nginx nginx \
  && rm -rf /opt/* \
  && apk del .build-deps

COPY rootfs /

FROM scratch

COPY --from=build / /

EXPOSE 80 443

ENTRYPOINT ["/init"]