Basic Docker Image
==================

The basic docker image serves as the starting point for creating further docker images that
implement the final toolchain. The intent of the basic image is that it contains all the tools
required to build software that are more or less stable, i.e. that will not change frequently in
the development cycle or when working with a cross toolchain and on a native Linux OS.

Note: The created image is set to the local timezone of Europe/Berlin.

Included Tools
==============

Basics
------

The following basic tools are included:
* Ubuntu 18.04 base
* Python 3
* pip3
* curl
* wget
* vim

SW Development Tools
------------

* Clang-tidy
* CMake 3.15.2
* Doxygen & Graphviz
* make