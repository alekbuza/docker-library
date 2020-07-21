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


include ../../../Makefile

USERNAME=aleksandarbuza
NAME=python
TAG=3.8.0
DOCKER_FILE_PATH=../Dockerfile
DOCKER_BUILD_ARGS= \
	--build-arg ALPINELINUX_TAG=3.12.0 \
	--build-arg GPG_KEY=E3FF2839C048B25C084DEBE9B26995E310250568 \
	--build-arg PYTHON_VERSION=3.8.0 \
	--build-arg PYTHON_PIP_VERSION=19.3.1 \
	--build-arg PYTHON_GET_PIP_URL=https://github.com/pypa/get-pip/raw/ffe826207a010164265d9cc807978e3604d18ca0/get-pip.py \
	--build-arg PYTHON_GET_PIP_SHA256=b86f36cc4345ae87bfd4f10ef6b2dbfa7a872fbff70608a1e43944d283fd0eee
