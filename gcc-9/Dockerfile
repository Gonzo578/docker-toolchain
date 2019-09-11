FROM toolchain/ubuntu-18.04-cmake-3.15:latest

LABEL maintainer="Ralf Hochhausen <micro@ralf-hochhausen.de>"

RUN apt-add-repository -y ppa:ubuntu-toolchain-r/test \
 && apt-get update \
 && apt-get install -y --no-install-recommends \
    gcc-9 \
    g++-9 \
    gdb \
    linux-tools-generic \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* \
 && ln -sf /usr/bin/g++-9 /usr/bin/g++ \
 && ln -sf /usr/bin/gcc-9 /usr/bin/gcc

ENV CC gcc
ENV CXX g++