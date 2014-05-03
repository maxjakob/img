# Julia Development environment
#
#   docker run -i \
#     -v $(pwd):/srv/julia
#     -w /srv/julia
#     -t purzelrakete/julia-dev /bin/bash
#
FROM ubuntu:14.04

MAINTAINER purzelrakete@gmail.com

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y software-properties-common
RUN add-apt-repository ppa:staticfloat/julianightlies
RUN add-apt-repository ppa:staticfloat/julia-deps
RUN apt-get update

RUN DEBIAN_FRONTEND=noninteractive apt-get -q -y build-dep julia
RUN DEBIAN_FRONTEND=noninteractive apt-get -q -y install git curl

VOLUME /srv/julia
RUN echo \
 USE_SYSTEM_LLVM=1 \\n \
 USE_SYSTEM_LIGHTTPD=1 \\n \
 USE_SYSTEM_LIBUNWIND=1 \\n \
 USE_SYSTEM_READLINE=1 \\n \
 USE_SYSTEM_PCRE=1 \\n \
 USE_SYSTEM_BLAS=1 \\n \
 USE_SYSTEM_LAPACK=1 \\n \
 USE_SYSTEM_FFTW=1 \\n \
 USE_SYSTEM_GMP=1 \\n \
 USE_SYSTEM_ARPACK=1 \\n \
 USE_SYSTEM_SUITESPARSE=1 \\n \
 USE_SYSTEM_NGINX=1 \\n\
 USE_SYSTEM_ZLIB=1 | sed 's/^ //' > Make.user

# starting docker as suggested in comments replaces everything in /srv/julia
RUN echo cp /Make.user /srv/julia > ~/.bashrc
