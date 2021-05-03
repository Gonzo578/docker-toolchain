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
 && update-alternatives --install /usr/bin/cc cc /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-gcc 100 \
 && update-alternatives --install /usr/bin/g++ g++ /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-g++ 100 \
 && update-alternatives --install /usr/bin/c++ c++ /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-c++ 100 \
 && update-alternatives --install /usr/bin/ar ar /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-ar 100 \
 && update-alternatives --install /usr/bin/as as /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-as 100 \
 && update-alternatives --install /usr/bin/ranlib ranlib /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-ranlib 100 \
 && update-alternatives --install /usr/bin/nm nm /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-nm 100 \
 && update-alternatives --install /usr/bin/ld ld /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-ld 100 \
 && update-alternatives --install /usr/bin/gcov gcov /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-gcov 100 \
 && update-alternatives --install /usr/bin/objdump objdump /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-objdump 100 \
 && update-alternatives --install /usr/bin/objcopy objcopy /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-objcopy 100 \
 && update-alternatives --install /usr/bin/strip strip /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-strip 100 \
 && update-alternatives --install /usr/bin/size size /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-size 100 \
 && update-alternatives --install /usr/bin/readelf readelf /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-readelf 100 \
 && update-alternatives --install /usr/bin/addr2line addr2line /usr/bin/gcc-arm-none-eabi-8-2019-q3-update/bin/arm-none-eabi-addr2line 100 \
 && conan profile new default --detect