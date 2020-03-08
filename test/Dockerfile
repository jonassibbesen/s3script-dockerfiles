FROM ubuntu:18.04

MAINTAINER jsibbese@ucsc.edu

WORKDIR /home

### Install essential tools

RUN apt-get update && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
	wget time git unzip autoconf automake make cmake gcc g++ \
	python2.7 python-pip python-setuptools python3 python3-pip python3-setuptools && \
    rm -rf /var/lib/apt/lists/*

RUN pip3 install --upgrade pip
RUN	pip3 install --no-cache-dir requests awscli


### Add s3 run script

ADD run.sh /home
