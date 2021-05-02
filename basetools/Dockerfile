FROM ubuntu:18.04

LABEL maintainer="Ralf Hochhausen <micro@ralf-hochhausen.de>"

# *****************************************************************************
# Install the very basics and configure time zone inside the docker container
# *****************************************************************************

# Install correct time zone
ARG TIMEZONE='Europe/Berlin'

RUN echo $TIMEZONE > /etc/timezone && \
  apt-get update && apt-get install -y tzdata && \
  rm /etc/localtime && \
  ln -snf /usr/share/zoneinfo/$TIMEZONE /etc/localtime && \
  dpkg-reconfigure -f noninteractive tzdata && \
  apt-get clean

# Install basic tools
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    dirmngr \
    git \
    gpg-agent \
    make \
    python3 \
    python3-dev \
    python3-pip \
    python3-setuptools \
    software-properties-common \
    vim \
    wget \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
 
# Install snap tools
RUN apt update \
 && apt install -y snapd 

# Install python package manager
RUN pip3 install --upgrade pip \
 && hash -r pip3 \
 && pip3 install -I pyyaml~=3.12

# *****************************************************************************
# Add more SW dev specific tools
# Use separate layers for the tools in order to be quicker in building new
# images.
# *****************************************************************************

# *****************************************************************************
# Install clang tools
# *****************************************************************************
RUN apt update \
 && apt install clang-format clang-tidy -y --no-install-recommends

# *****************************************************************************
# Install cmake with a specific version
# *****************************************************************************

ARG MAJOR_VERSION=3
ARG MINOR_VERSION=15
ARG PATCH_VERSION=2
ARG VERSION="$MAJOR_VERSION.$MINOR_VERSION.$PATCH_VERSION"
ARG ARCH="Linux-x86_64"

RUN cd opt \
 && wget -q https://cmake.org/files/v$MAJOR_VERSION.$MINOR_VERSION/cmake-$VERSION-$ARCH.tar.gz \
 && tar xf cmake-$VERSION-$ARCH.tar.gz \
 && rm cmake-$VERSION-$ARCH.tar.gz \
 && ln -sf /opt/cmake-$VERSION-$ARCH/bin/ccmake /usr/bin/ccmake \
 && ln -sf /opt/cmake-$VERSION-$ARCH/bin/cmake /usr/bin/cmake \
 && ln -sf /opt/cmake-$VERSION-$ARCH/bin/cmake-gui /usr/bin/cmake-gui \
 && ln -sf /opt/cmake-$VERSION-$ARCH/bin/cpack /usr/bin/cpack \
 && ln -sf /opt/cmake-$VERSION-$ARCH/bin/ctest /usr/bin/ctest

# *****************************************************************************
# Install conan tools
# *****************************************************************************
 RUN   pip install -q --no-cache-dir conan conan-package-tools --upgrade
 
# *****************************************************************************
# Install doxygen
# Note: We don't insall doxygen with the latex package. This needs to be
# added manually
# *****************************************************************************
RUN apt-get update \
 && apt-get install -y --no-install-recommends doxygen \
 && apt-get install -y graphviz
