# Copyright (c) 2020 Aleksandar Buza <aleksandar.buza@qsafe.systems>
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

ARG ALPINELINUX_VERSION

FROM aleksandarbuza/alpinelinux:${ALPINELINUX_VERSION} as build

ARG S6_OVERLAY_URL
ARG S6_OVERLAY_GPGSIGN_URL

WORKDIR /opt

RUN set -ex \
	&& apk add --no-cache --virtual .fetch-deps \
    curl \
    gnupg \
		tar \
		xz \
  && wget -O s6-overlay.tar.gz $S6_OVERLAY_URL \
  && wget -O s6-overlay.tar.gz.sig $S6_OVERLAY_GPGSIGN_URL \
  && curl https://keybase.io/justcontainers/key.asc | gpg --import \
  && gpg --verify s6-overlay.tar.gz.sig s6-overlay.tar.gz \
  && tar xfz s6-overlay.tar.gz -C / \
  && rm -rf /opt/* \
  && apk del .fetch-deps

FROM scratch

COPY --from=build / /

ENTRYPOINT ["/init"]
