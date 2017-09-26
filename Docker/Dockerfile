FROM ubuntu:16.04

ENV TERM xterm
RUN apt-get update && apt-get -y dist-upgrade && apt-get clean && apt-get -y autoremove
RUN apt-get update && apt-get install -y  software-properties-common
RUN add-apt-repository ppa:openjdk-r/ppa
RUN apt-get update && apt-get install -y \
	bc \
	gcc \
	gcc-arm-linux-gnueabi \
	gcc-aarch64-linux-gnu \
    gcc-arm-linux-gnueabihf \
	libncurses5-dev \
    curl \ 
    kpartx \
    android-tools-fsutils \
	make \
    sudo \
    device-tree-compiler \
    wget \ 
	python

ENV CROSS_COMPILE aarch64-linux-gnu-
ENV ARCH arm64
# where we build
RUN mkdir /source
VOLUME ["/source"]
WORKDIR /source

CMD ["/bin/bash"]
