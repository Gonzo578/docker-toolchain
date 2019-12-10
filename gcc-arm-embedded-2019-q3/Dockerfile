FROM toolchain/ubuntu-18.04-cmake-3.10:latest

LABEL maintainer="Ralf Hochhausen <micro@ralf-hochhausen.de>"

RUN cd usr/bin \
 && wget -q https://developer.arm.com/-/media/Files/downloads/gnu-rm/8-2019q3/RC1.1/gcc-arm-none-eabi-8-2019-q3-update-linux.tar.bz2 \
 && tar -xjf gcc-arm-none-eabi-8-2019-q3-update-linux.tar.bz2 \
 && rm gcc-arm-none-eabi-8-2019-q3-update-linux.tar.bz2
 