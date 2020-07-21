# Copyright (c) 2019, 2020 Aleksandar Buza <aleksandar.buza@qsafe.systems>
#
# Permission to use, copy, modify, and distribute this software for any
# purpose with or without fee is hereby granted, provided that the above
# copyright notice and this permission notice appear in all copies.
#
# THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
# WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
# MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
# ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
# WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
# ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
# OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.


FROM aleksandarbuza/alpinelinux:latest as build

# http://dl-cdn.alpinelinux.org/alpine
ARG ALPINELINUX_URL

# Example: v3.11
ARG ALPINELINUX_RELEASE

# Example: 3.11.3
ARG ALPINELINUX_VERSION

# Example: x86_64
ARG ALPINELINUX_ARCH

WORKDIR /opt

RUN set -ex \
    && apk add --no-cache --virtual .fetch-deps curl wget \
    && FILES=$(curl -s $ALPINELINUX_URL/$ALPINELINUX_RELEASE/releases/$ALPINELINUX_ARCH/ | grep "alpine-minirootfs-$ALPINELINUX_VERSION-$ALPINELINUX_ARCH" | sed -n 's/.*href="\([^"]*\).*/\1/p' | awk '{print $(NF)}' | tail -4) \
    && for FILE in $FILES; do wget $ALPINELINUX_URL/$ALPINELINUX_RELEASE/releases/$ALPINELINUX_ARCH/$FILE; done \
    && sha256sum -c *.tar.gz.sha256 \
    && sha512sum -c *.tar.gz.sha512 \
    && mkdir /rootfs \
    && gzip -dc *.tar.gz | tar -xf - -C /rootfs

FROM scratch

COPY --from=build /rootfs /
