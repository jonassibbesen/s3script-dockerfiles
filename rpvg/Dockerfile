FROM jsibbesen/vgdev-s3script:cf189f38-s1

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install essential tools (including protobuf)

RUN apt-get update && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
	pkg-config protobuf-compiler libprotoc-dev libprotobuf-dev libjansson-dev && \
    rm -rf /var/lib/apt/lists/*

### Install newer htslib 

RUN wget --no-check-certificate https://github.com/samtools/htslib/releases/download/1.11/htslib-1.11.tar.bz2 && \
	tar -xvjf htslib-1.11.tar.bz2 && \
	cd htslib-1.11 && \
	./configure && \
	make install && \
 	cd .. && \
 	rm -r htslib*

WORKDIR /

### Install rpvg 

RUN GIT_SSL_NO_VERIFY=true git clone --recursive https://github.com/jonassibbesen/rpvg.git && \
	cd rpvg && \
	git checkout 1f6b89e1a3884c100fe179f0eee1c2a17a29c2ea && \
	cmake . && \
	make && \
	cd ..

WORKDIR /home
