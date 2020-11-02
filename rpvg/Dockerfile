FROM quay.io/vgteam/vg:ci-2493-cf189f38eddd161cd4d37c5f9c8b890e10b335d2

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install essential tools (including protobuf)

RUN apt-get update && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
	pkg-config protobuf-compiler libprotoc-dev libprotobuf-dev && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /

### Install rpvg 

RUN GIT_SSL_NO_VERIFY=true git clone --recursive https://github.com/jonassibbesen/rpvg.git && \
	cd rpvg && \
	git checkout e75a5bdd4c0c370aac3b4d6944c77af7c681ff63 && \
	cmake . && \
	make && \
	cd ..

WORKDIR /home
