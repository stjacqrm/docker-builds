FROM ubuntu:xenial

LABEL base.image="ubuntu:xenial"
LABEL container.version="2"
LABEL software="QUAST"
LABEL software.version="5.0.2"
LABEL description="Genome assembly evaluation tool"
LABEL website="https://github.com/ablab/quast"
LABEL license="https://github.com/ablab/quast/blob/master/LICENSE.txt"
LABEL maintainer="Curtis Kapsak"
LABEL maintainer.email="pjx8@cdc.gov"

RUN apt-get update && apt-get install -y zlib1g-dev \
  pkg-config \
  libfreetype6-dev \
  libpng-dev \
  wget \
  g++ \
  make \
  perl \
  python \
  python-setuptools \
  python-matplotlib \
  python-simplejson \
  python-joblib \
  locales \
  python-pip && \
  locale-gen en_US.UTF-8 && \
  apt-get clean && \
  apt-get autoclean && \
  rm -rf /var/lib/apt/lists/*

ENV LC_ALL=C

RUN python -m pip install -U pip

RUN wget https://github.com/ablab/quast/releases/download/quast_5.0.2/quast-5.0.2.tar.gz && \
    tar -xzf quast-5.0.2.tar.gz && \
    rm -rf quast-5.0.2.tar.gz && \
    cd /quast-5.0.2 && \
    /quast-5.0.2/setup.py install && \
    mkdir /data

WORKDIR /data
