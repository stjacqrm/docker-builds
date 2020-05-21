
FROM ubuntu:xenial

# metadata
LABEL base.image="ubuntu:xenial"
LABEL version="1"
LABEL software="NanoStat"
LABEL software.version="1.2.0"
LABEL description="Calculate various statistics from a long read sequencing dataset in fastq, bam or albacore sequencing summary format"
LABEL website="https://github.com/wdecoster/NanoStat"
LABEL license="https://github.com/wdecoster/NanoStat/blob/master/LICENSE"
LABEL maintainer="Rachael St. Jacques"
LABEL maintainer.email="rachael.stjacques@dgs.virginia.gov"

RUN apt-get update && apt-get install -y zlib1g-dev \
  bzip2 \
  libbz2-dev \
  liblzma-dev \
  libcurl4-gnutls-dev \
  libncurses5-dev \
  libssl-dev \
  python3 \
  python3-pip \
  python3-setuptools \
  locales && \
  locale-gen en_US.UTF-8 && \
  apt-get autoclean

# for singularity compatibility
ENV LC_ALL=C

# update pip, install NanoStat
RUN python3 -m pip install -U pip && \
  pip3 install requests NanoStat && \
  mkdir /data

ENV PATH="${PATH}:/NanoStat"


WORKDIR /data
