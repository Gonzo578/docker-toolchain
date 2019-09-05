FROM ubuntu:18.04

MAINTAINER Ralf Hochhausen <micro@ralf-hochhausen.de>

ARG TIMEZONE='Europe/Berlin'

RUN echo $TIMEZONE > /etc/timezone && \
  apt-get update && apt-get install -y tzdata && \
  rm /etc/localtime && \
  ln -snf /usr/share/zoneinfo/$TIMEZONE /etc/localtime && \
  dpkg-reconfigure -f noninteractive tzdata && \
  apt-get clean
