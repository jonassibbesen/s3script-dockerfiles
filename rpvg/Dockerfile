FROM quay.io/jsibbesen/vgdev-s3script:vgdev-883f0f87-s1

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install essential tools (including protobuf)

RUN apt-get update && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
	pkg-config protobuf-compiler libprotoc-dev libprotobuf-dev libjansson-dev && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /

### Install rpvg 

RUN GIT_SSL_NO_VERIFY=true git clone --recursive https://github.com/jonassibbesen/rpvg.git && \
	cd rpvg && \
	git checkout 1111b7f99ea0180d31f8a28c7c453186822d6066 && \
	GIT_SSL_NO_VERIFY=true git submodule update --init --recursive && \
	cmake . && \
	make && \
	cd ..

WORKDIR /home
