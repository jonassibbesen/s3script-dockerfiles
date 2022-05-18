FROM quay.io/jsibbesen/vgdev-s3script:vgdev-2cea1e25-s2

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install R

RUN apt-get update && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
	r-base r-base-dev && \
    rm -rf /var/lib/apt/lists/*

### Install pysam and biopython

RUN pip3 install --upgrade pip
RUN	pip3 install --no-cache-dir pysam biopython

### Install vgrna scripts 

RUN git clone https://github.com/jonassibbesen/vgrna-project-scripts.git && \
	cd vgrna-project-scripts && \
	git checkout f63f9df20b6d33d3c09ef3bc2293acb56e02aef8 && \
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
