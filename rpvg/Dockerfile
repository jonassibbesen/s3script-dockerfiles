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
	git checkout 6cf2224af8c82d67bb04a2ed06cda71e4e355b72 && \
	GIT_SSL_NO_VERIFY=true git submodule update --init --recursive && \
	cmake . && \
	make && \
	cd ..

WORKDIR /home
