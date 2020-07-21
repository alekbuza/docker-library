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
NAME=ansible
TAG=2.9.9
DOCKER_FILE_PATH=../Dockerfile
DOCKER_BUILD_ARGS=\
	--build-arg ANSIBLE_TARBALL_URL=https://releases.ansible.com/ansible/ansible-2.9.9.tar.gz \
	--build-arg ANSIBLE_TARBALL_SHA256=e83d84ae8bf131c0499d8a4c0e1144bf969454c43086e61cca3c224227df29d1 \
	--build-arg ANSIBLE_UID=1000 \
	--build-arg ANSIBLE_GID=1000
