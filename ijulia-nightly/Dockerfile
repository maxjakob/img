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

RUN DEBIAN_FRONTEND=noninteractive apt-get -q -y install sudo julia

RUN julia -e 'Pkg.add("IJulia")'

ADD ijulia /usr/bin/ijulia

EXPOSE 8888
