FROM quay.io/jsibbesen/vgdev-s3script:vgdev-385fd636-s2

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install essential tools (including protobuf)

RUN apt-get update && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
	pkg-config protobuf-compiler libprotoc-dev libprotobuf-dev libjansson-dev && \
    rm -rf /var/lib/apt/lists/*

### Install rpvg 

RUN GIT_SSL_NO_VERIFY=true git clone --recursive https://github.com/jonassibbesen/rpvg.git && \
	cd rpvg && \
	git checkout 00c856f38a44cb34830501bf64d66d94eb484240 && \
	GIT_SSL_NO_VERIFY=true git submodule update --init --recursive && \
	mkdir build && \
	cd build && \
	cmake .. && \
	make && \
	cd ../../ && \
	mv rpvg/bin/rpvg /usr/bin/ && \
	unlink rpvg/deps/libvgio/vg
