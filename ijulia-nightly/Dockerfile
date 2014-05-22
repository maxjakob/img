# Start with `bin/ijulia --start` and open http://localhost:8888. Notebooks
# will be saved and served out of the current host directory.
#
# Get it at http://github.com/purzelrakete/img/bin/ijulia.
#

FROM purzelrakete/ipython

MAINTAINER Rany Keddo <purzelrakete@gmail.com>

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y software-properties-common
RUN add-apt-repository ppa:staticfloat/julianightlies
RUN add-apt-repository ppa:staticfloat/julia-deps
RUN apt-get update

RUN DEBIAN_FRONTEND=noninteractive apt-get -q -y install \
  curl \
  gettext \
  git \
  julia \
  libnettle4 \
  sudo \
  tmux \
  vim \
  wget

ENV HOME /root
ADD REQUIRE /root/.julia/v0.3/REQUIRE
ADD ijulia /usr/bin/ijulia

RUN julia -e 'Pkg.init(); Pkg.resolve();'

EXPOSE 8888
