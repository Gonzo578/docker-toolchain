FROM toolchain/ubuntu-18.04-cmake-3.10:latest

LABEL maintainer="Ralf Hochhausen <micro@ralf-hochhausen.de>"

RUN cd usr/bin \
 && wget -q https://developer.arm.com/-/media/Files/downloads/gnu-rm/9-2019q4/RC2.1/gcc-arm-none-eabi-9-2019-q4-major-x86_64-linux.tar.bz2 \
 && tar -xjf gcc-arm-none-eabi-9-2019-q4-major-x86_64-linux.tar.bz2 \
 && rm gcc-arm-none-eabi-9-2019-q4-major-x86_64-linux.tar.bz2
 