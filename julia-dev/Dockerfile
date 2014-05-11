# Julia development environment
#
# Fork and check out your fork into a local directory. Switch into this
# directory and start a container:
#
#   docker run -i \
#     -v $(pwd):/srv/julia
#     -w /srv/julia
#     -t purzelrakete/julia-dev /bin/bash
#
# You can work on the host machine and `make` inside the guest.
#
FROM ubuntu:12.04

MAINTAINER purzelrakete@gmail.com

RUN apt-get update -qq -y
RUN apt-get install -y zlib1g-dev git curl

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y python-software-properties
RUN add-apt-repository -y ppa:staticfloat/julia-deps
RUN apt-get update -qq -y

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y patchelf gfortran \
  llvm-3.3-dev libsuitesparse-dev libopenblas-dev liblapack-dev \
  libarpack2-dev libfftw3-dev libgmp-dev libpcre3-dev libunwind7-dev \
  libdouble-conversion-dev libopenlibm-dev librmath-dev libmpfr-dev

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y make g++ vim

VOLUME /srv/julia
RUN echo \
  LLVM_CONFIG=llvm-config-3.3 \\n \
  LLVM_LLC=llc-3.3 \\n \
  USE_BLAS64=0 \\n \
  USE_SYSTEM_ARPACK=1 \\n \
  USE_SYSTEM_BLAS=1 \\n \
  USE_SYSTEM_FFTW=1 \\n \
  USE_SYSTEM_GMP=1 \\n \
  USE_SYSTEM_GRISU=1 \\n \
  USE_SYSTEM_LAPACK=1 \\n \
  USE_SYSTEM_LIBUNWIND=1 \\n \
  USE_SYSTEM_LLVM=1 \\n \
  USE_SYSTEM_MPFR=1 \\n \
  USE_SYSTEM_OPENLIBM=1 \\n \
  USE_SYSTEM_PCRE=1 \\n \
  USE_SYSTEM_SUITESPARSE=1 \\n \
  USE_SYSTEM_ZLIB=1 \\n \
  USE_SYSTEM_RMATH=1 | tr -d ' ' > /root/Make.user

# starting docker as suggested above replaces everything in /srv/julia
ENV HOME /root
RUN echo "cp /root/Make.user /srv/julia && cd /srv/julia" >> /root/.bashrc

