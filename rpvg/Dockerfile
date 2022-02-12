FROM quay.io/jsibbesen/vgdev-s3script:vgdev-cb090f0c-s2

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
	git checkout 0380bdb172bbe255a18ed070935fa0013dc02548 && \
	GIT_SSL_NO_VERIFY=true git submodule update --init --recursive && \
	mkdir build && \
	cd build && \
	cmake .. && \
	make && \
	cd ../../ && \
	mv rpvg/bin/rpvg /usr/bin/ && \
	unlink rpvg/deps/libvgio/vg
