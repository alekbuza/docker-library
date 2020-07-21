# Copyright (c) 2019, 2020 Aleksandar Buza <aleksandar.buza@qsafe.systems>
# Copyright (c) 2020 Jovan Markovic <jovan.markovic@qsafe.systems>
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


FROM aleksandarbuza/python:3.8.0 as build

ARG ANSIBLE_UID
ARG ANSIBLE_GID
ARG ANSIBLE_TARBALL_URL
ARG ANSIBLE_TARBALL_SHA256

WORKDIR /opt

RUN set -ex \
    && addgroup -g $ANSIBLE_GID -S ansible \
    && adduser -u $ANSIBLE_UID -S ansible -G ansible \
    && apk add --no-cache openssh-client \
    && apk add --no-cache --virtual .build-deps \
        linux-headers \
        gcc \
        musl-dev \
        libffi-dev \
        openssl-dev \
        yaml-dev \
    && wget -O ansible.tar.gz $ANSIBLE_TARBALL_URL \
    && echo "$ANSIBLE_TARBALL_SHA256  ansible.tar.gz" > ansible.tar.gz.sha \
    && cat ansible.tar.gz.sha \
    && sha256sum -c ansible.tar.gz.sha \
    && tar -xvzf ansible.tar.gz && cd ansible-* \
    && python setup.py install \
    && cd / && rm -rf /opt/* \
    && apk del .build-deps \
    && mkdir -p /ansible-ops

RUN ansible --version

FROM scratch

COPY --from=build / /

USER ansible

WORKDIR /ansible-ops
