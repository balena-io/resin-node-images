FROM resin/armv7hf-debian:wheezy

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update \
	&& apt-get install -y \
		build-essential \
		wget \
		python \
		python-dev \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists

ENV NODE_VERSION 0.11.2

RUN	cd /tmp \
	&& wget -O- --quiet http://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION.tar.gz | tar xz \
	&& cd node-v$NODE_VERSION \
	&& ./configure --without-snapshot \
	&& make -j $(nproc) \
	&& make install \
	&& cd /tmp \
	&& rm -rf /tmp/node-v$NODE_VERSION \
	&& npm install -g npm \
	&& npm cache clean

CMD [ "/bin/bash", "-c" ]
