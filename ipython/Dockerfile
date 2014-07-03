FROM ubuntu:precise

MAINTAINER Rany Keddo <purzelrakete@gmail.com>

# apt
RUN apt-get update
RUN apt-get install -y python-software-properties
RUN add-apt-repository -y ppa:pythonxy/pythonxy-devel
RUN add-apt-repository -y ppa:jtaylor/ipython-dev
RUN apt-get update

# base ipython packages
RUN apt-get install -y ipython ipython-notebook \
  python-numpy python-pip python-matplotlib python-pandas python-nose
RUN apt-get install -y gfortran libopenblas-dev liblapack-dev

# python
RUN pip install --upgrade scipy
RUN pip install patsy
RUN pip install statsmodels
RUN pip install bokeh
RUN pip install pylint==1.2.0

ADD ipython-start /usr/bin/ipython-start
