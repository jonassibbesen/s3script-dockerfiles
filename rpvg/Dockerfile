FROM quay.io/jsibbesen/vgdev-s3script:vgdev-c4bbd63b-s1

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
	git checkout 81ea2f25b840c3a5bb05257a104c83ce6ba7a8ab && \
	GIT_SSL_NO_VERIFY=true git submodule update --init --recursive && \
	cmake . && \
	make -j 2 && \
	cd ..

WORKDIR /home
