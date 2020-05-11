FROM jsibbesen/base-s3script:18.04-s1

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install vg 

RUN wget --no-check-certificate https://github.com/vgteam/vg/releases/download/v1.24.0/vg && \
	chmod +x vg && \
	mv vg /usr/bin/

RUN wget --no-check-certificate https://github.com/vgteam/vg/releases/download/v1.24.0/vg-v1.24.0.tar.gz && \
	tar -xzvf vg-v1.24.0.tar.gz && \
	mkdir -p /scripts/vg/ && \
	mv vg-v1.24.0/scripts/* /scripts/vg/ && \
	rm -r vg*
