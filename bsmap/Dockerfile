################## BASE IMAGE #############################
FROM ubuntu:18.04

################## METADATA ###############################
LABEL base_image="ubuntu:18.04"
LABEL version="1"
LABEL software="BSMAP"
LABEL software.version="2.90"
LABEL about.summary="Bisulfite Sequence Mapping Program"
LABEL about.home="https://code.google.com/archive/p/bsmap/"
LABEL about.documentation="https://code.google.com/archive/p/bsmap/"
LABEL about.license_file="https://www.gnu.org/licenses/gpl-3.0.html"
LABEL about.license="GNU GPLv3"
LABEL extra.identifiers.biotools="BSMAP"
LABEL about.tags="Methylation, Epigenomics, Bisulfite sequencing, Genomics, NGS, Mapping"

################## MAINTAINER #############################
MAINTAINER Pandurang Kolekar <pandurang.kolekar@gmail.com>

################## INSTALLATION ###########################
RUN apt-get update && apt-get install -y \
  build-essential \
  wget \
  python2.7 \
  python-pip \
  libz-dev

# Download & extract bsmap archive
RUN wget http://lilab.research.bcm.edu/dldcc-web/lilab/yxi/bsmap/bsmap-2.90.tgz && \
  tar zxfv bsmap-2.90.tgz && \
  rm bsmap-2.90.tgz

# Install bsmap
RUN cd bsmap-2.90 && \
  make && \
  make install && \
  chmod a+x bsmap

# Include it in PATH
ENV PATH /bsmap-2.90:$PATH
