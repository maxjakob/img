# Start the notebook:
#
#   docker run \
#     -v $(pwd):/srv/app  \
#     -w /srv/app \
#     -p 8888:8888 \
#     -t purzelrakete/ijulia-nightly \
#     ijulia
#
# The notebook will be available at http://localhost:8888/. Notebooks will be
# saved and served out of the current host directory.
#
# Note that if your are using boot2docker on OSX, you may have to fiddle with
# forwarded ports:
#
# https://github.com/boot2docker/boot2docker/blob/master/doc/WORKAROUNDS.md
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
  sudo \
  tmux \
  vim \
  wget

RUN julia -e 'Pkg.update();'
RUN julia -e 'Pkg.add("IJulia");'
RUN julia -e 'Pkg.add("Distributions");'
RUN julia -e 'Pkg.add("Gadfly");'
RUN julia -e 'Pkg.add("DataFrames");'
RUN julia -e 'Pkg.add("PyCall");'
RUN julia -e 'Pkg.add("Winston");'
RUN julia -e 'Pkg.add("Graphs");'
RUN julia -e 'Pkg.add("StatsBase");'
RUN julia -e 'Pkg.add("MCMC");'
RUN julia -e 'Pkg.add("TextAnalysis");'

ADD ijulia /usr/bin/ijulia

EXPOSE 8888
