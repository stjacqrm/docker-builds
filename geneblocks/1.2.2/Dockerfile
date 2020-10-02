# base image
FROM ubuntu:bionic

# metadata
LABEL base.image="ubuntu:bionic"
LABEL version="1"
LABEL software="BCBio"
LABEL software.version="0.6.5"
LABEL description="Collection of useful code related to biological analysis and NC_045512.2 gb file."
LABEL website="https://github.com/chapmanb/bcbb"
LABEL license="https://opensource.org/licenses/MIT"
LABEL maintainer="Rachael St. Jacques"
LABEL maintainer.email="rachael.stjacques@dgs.virginia.gov"

RUN apt-get update && apt-get -y --no-install-recommends install \
    unzip \
    tar \
    python3.5 \
    python3-pip \
    #python-setuptools \
    gzip \
    python3-dev \
    build-essential \
    libssl-dev \
    libffi-dev \
    libxml2-dev \
    libxslt1-dev \
    zlib1g-dev \
    wget && \
    apt-get clean

#grab genbank file
RUN wget https://github.com/stjacqrm/gb_files/archive/9f32c86c209aab5a5157503d607ee7ed66f81ad3.zip &&\
    unzip 9f32c86c209aab5a5157503d607ee7ed66f81ad3.zip &&\
    mv gb_files-9f32c86c209aab5a5157503d607ee7ed66f81ad3 gb_files &&\
    mkdir /reference &&\
    mv /gb_files/NC_045512_2.gb /reference

#install the software
RUN wget https://github.com/chapmanb/bcbb/archive/3ba0ec42120065cca136fd496948948f57081039.zip &&\
    unzip 3ba0ec42120065cca136fd496948948f57081039.zip &&\
    mv bcbb-3ba0ec42120065cca136fd496948948f57081039 BCBio &&\
    chmod 777 -R BCBio &&\
    mkdir /data


RUN pip3 install wheel==0.35.1 biopython==1.77 setuptools==50.0.0 matplotlib==3.3.2

RUN pip3 install bcbio-gff==0.6.6 geneblocks==1.2.2

RUN ln -s /usr/bin/python3 /usr/bin/python


#install the software
RUN wget https://github.com/Edinburgh-Genome-Foundry/Geneblocks/archive/v1.2.2.zip &&\
    unzip v1.2.2.zip &&\
    mv Geneblocks-1.2.2 Geneblocks &&\
    chmod 777 -R Geneblocks &&\
    cd Geneblocks &&\
    python setup.py install

# blast 2.9.0 (blast in apt for ubuntu:bionic is v2.6.0 from 2017)
RUN wget ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.9.0/ncbi-blast-2.9.0+-x64-linux.tar.gz && \
    tar -xzf ncbi-blast-2.9.0+-x64-linux.tar.gz && \
    rm ncbi-blast-2.9.0+-x64-linux.tar.gz

#set paths
ENV PATH="/BCBio:\
/BCBio/gff/Scripts/gff:\
/reference:\
/Geneblocks/bin:\
/ncbi-blast-2.9.0+/bin:\
$PATH"\
    LC_ALL=C

WORKDIR /data
