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

# Install python package manager
RUN pip3 install --upgrade pip \
 && hash -r pip3 \
 && pip3 install -I pyyaml~=3.12

# *****************************************************************************
# Add more SW dev specific tools
# Use separate layers for the tools in order to be quicker in building new
# images.
# *****************************************************************************

# Install clang-tidy code checker
RUN apt update \
 && apt install clang-tidy -y --no-install-recommends


