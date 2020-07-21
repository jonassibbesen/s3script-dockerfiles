FROM jsibbesen/base-s3script:18.04-s1

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install salmon 

RUN wget --no-check-certificate https://github.com/COMBINE-lab/salmon/releases/download/v1.2.1/salmon-1.2.1_linux_x86_64.tar.gz && \
	tar -xvzf salmon-1.2.1_linux_x86_64.tar.gz && \
	cd salmon-latest_linux_x86_64 && \
	mv bin/salmon /usr/bin/ && \
	mv lib/* /usr/lib/ && \
	cd .. && \
 	rm -r salmon*
