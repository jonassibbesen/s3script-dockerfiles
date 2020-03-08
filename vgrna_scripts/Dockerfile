FROM jsibbesen/base-s3script:18.04-s1

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install R

RUN apt-get update && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
	r-base r-base-dev && \
    rm -rf /var/lib/apt/lists/*

### Install pysam

RUN pip3 install --upgrade pip
RUN	pip3 install --no-cache-dir pysam

### Install vgrna scripts 

RUN git clone https://github.com/jonassibbesen/vgrna-project-scripts.git && \
	cd vgrna-project-scripts && \
	git checkout d036d0dc1a90e6449911351d744e0eea09db0a49 && \
	cd c++ && \
	cmake . && \
	make && \
	mv bin/* /usr/bin/ && \
	cd .. && \
	mkdir -p /scripts/vgrna/ && \
	mv python/*.py /scripts/vgrna/ && \
	mv R/*.R /scripts/vgrna/ && \
	mv .git/ /scripts/vgrna/ && \
	cd .. && \
 	rm -r vgrna-project-scripts
