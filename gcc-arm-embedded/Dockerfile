# *****************************************************************************
# Derive from based tools docker image which already includes many SW tools
# Just add the concrete compiler version to it
# *****************************************************************************
FROM toolchain/basetools:latest

LABEL maintainer="Ralf Hochhausen <micro@ralf-hochhausen.de>"

ENV PATH=/usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin:${PATH} \
    CC=arm-none-eabi-gcc \
    CXX=arm-none-eabi-g++ \
    CMAKE_C_COMPILER=arm-none-eabi-gcc \
    CMAKE_CXX_COMPILER=arm-none-eabi-g++ \
    STRIP=arm-none-eabi-strip \
    RANLIB=arm-none-eabi-ranlib\
    AS=arm-none-eabi-as \
    AR=arm-none-eabi-ar \
    LD=arm-none-eabi-ld

# *****************************************************************************
# Install arm-gcc toolchain for Cortex M MCUs
# Version 2019-q3
# *****************************************************************************
RUN cd usr/bin \
 && wget -q https://developer.arm.com/-/media/Files/downloads/gnu-rm/8-2019q3/RC1.1/gcc-arm-none-eabi-8-2019-q3-update-linux.tar.bz2 \
 && tar -xjf gcc-arm-none-eabi-8-2019-q3-update-linux.tar.bz2 \
 && rm gcc-arm-none-eabi-8-2019-q3-update-linux.tar.bz2 \
 && conan profile new default --detect