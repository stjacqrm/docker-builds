FROM ubuntu:bionic

# metadata
LABEL base.image="ubuntu:bionic"
LABEL container.version="1"
LABEL software="Augur"
LABEL software.version="6.3.0"
LABEL description="Pipeline components for real-time phylodynamic analysis"
LABEL website="https://github.com/nextstrain/augur"
LABEL license="https://github.com/nextstrain/augur/blob/master/LICENSE.txt"
LABEL maintainer="Kelsey Florek"
LABEL maintainer.email="kelsey.florek@slh.wisc.edu"

RUN apt-get update && apt-get install -y python3 \
  wget\
  python3-pip\
  iqtree\
  build-essential\
  zlib1g-dev\
  pkg-config\
  mafft

RUN wget https://github.com/vcftools/vcftools/releases/download/v0.1.16/vcftools-0.1.16.tar.gz &&\
  tar -xzf vcftools-0.1.16.tar.gz &&\
  rm vcftools-0.1.16.tar.gz &&\
  cd vcftools-0.1.16 &&\
  ./configure &&\
  make && make install

RUN wget https://github.com/nextstrain/augur/archive/6.3.0.tar.gz && \
  tar -xzf 6.3.0.tar.gz && \
  pip3 install /augur-6.3.0/ && \
  mkdir /data

WORKDIR /data
