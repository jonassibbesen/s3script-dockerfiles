FROM jsibbesen/base-s3script:18.04-s1

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install hisat2 

RUN wget --no-check-certificate https://cloud.biohpc.swmed.edu/index.php/s/hisat2-220-Linux_x86_64/download && \
	unzip download && \
	cd hisat2-2.2.0 && \
	make && \
	mv hisat2 /usr/bin/ && \
	mv hisat2-* /usr/bin/ && \
	mkdir -p /scripts/hisat2/ && \
	mv *py /scripts/hisat2/ && \
	mv scripts/* /scripts/hisat2/ && \
	mv hisatgenotype_*/* /scripts/hisat2/ && \
	cd .. && \
	rm -r download* && \
	rm -r hisat2-2.2.0*
