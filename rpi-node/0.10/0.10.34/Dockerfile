FROM resin/rpi-raspbian:wheezy

ENV DEBIAN_FRONTEND noninteractive
ENV NODE_VERSION 0.10.34

RUN apt-get update && apt-get install -y \
							build-essential \
							wget \
							python \
							python-dev \
					&& apt-get clean \
					&& rm -rf /var/lib/apt/lists

RUN	cd /tmp && \
  	wget http://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION.tar.gz && \
	tar xvzf node-v$NODE_VERSION.tar.gz && \
	rm -f node-v$NODE_VERSION.tar.gz && \
	cd node-v* && \
	./configure --without-snapshot && \
	make && \
	make install && \
	cd /tmp && \
	rm -rf /tmp/node-v* && \
	npm install -g npm
	
CMD [ "/bin/bash", "-c" ]