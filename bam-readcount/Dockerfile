################## BASE IMAGE #############################
FROM ubuntu:18.04

################## METADATA ###############################
LABEL base_image="ubuntu"
LABEL version="18.04"
LABEL software="bam-readcount"
LABEL about.summary="Compute position wise nucleotide counts from BAM file"
LABEL about.home="https://github.com/genome/bam-readcount"
LABEL about.license_file="MIT"
LABEL about.tags="NGS BAM readcount"

################## MAINTAINER #############################
MAINTAINER Pandurang Kolekar <pandurang.kolekar@gmail.com>

################## INSTALLATION ###########################
RUN apt-get update \
  && apt-get -y install build-essential git-core cmake zlib1g-dev libncurses-dev patch \
  && rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/genome/bam-readcount.git \
  && cd bam-readcount/ \
  && cmake ./ && make
ENV PATH="/bam-readcount/bin:${PATH}"

WORKDIR /bam-readcount/bin

ENTRYPOINT ["/bin/bash"]
