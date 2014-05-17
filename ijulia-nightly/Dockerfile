# Start the notebook:
#
#   docker run \
#     -v $(pwd):/srv/app  \
#     -w /srv/app \
#     -p 8080:8888 \
#     -t purzelrakete/ijulia-nightly \
#     ipython notebook --profile ijulia
#
# The notebook will be available at http://localhost:8080/. Notebooks will be
# saved and served out of the current host directory.

FROM purzelrakete/ipython

MAINTAINER Rany Keddo <purzelrakete@gmail.com>

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y software-properties-common
RUN add-apt-repository ppa:staticfloat/julianightlies
RUN add-apt-repository ppa:staticfloat/julia-deps
RUN apt-get update

RUN DEBIAN_FRONTEND=noninteractive apt-get -q -y install sudo julia

RUN julia -e 'Pkg.add("IJulia")'
