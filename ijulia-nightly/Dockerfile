FROM purzelrakete/ipython

MAINTAINER Rany Keddo <purzelrakete@gmail.com>

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y software-properties-common
RUN add-apt-repository ppa:staticfloat/julianightlies
RUN add-apt-repository ppa:staticfloat/julia-deps
RUN apt-get update

RUN DEBIAN_FRONTEND=noninteractive apt-get -q -y install julia

RUN julia -e 'Pkg.add("IJulia")'
