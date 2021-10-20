FROM quay.io/jsibbesen/base-s3script:base-20.04-s2

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
	git checkout 0328277eb7ce57e81f29e51d3eaa9651997372bb && \
	GIT_SSL_NO_VERIFY=true git submodule update --init --recursive && \
	mkdir build && \
	cd build && \
	cmake .. && \
	make -j 4 && \
	cd ../../ && \
	mv rpvg/bin/rpvg /usr/bin/
