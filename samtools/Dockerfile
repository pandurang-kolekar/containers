################## BASE IMAGE #############################
FROM ubuntu:18.04

################## METADATA ###############################
LABEL base_image="ubuntu:18.04"
LABEL version="1"
LABEL software="samtools"
LABEL software.version="1.11"
LABEL about.summary="Tools (written in C using htslib) for manipulating next-generation sequencing data"
LABEL about.home="https://github.com/samtools/samtools"
LABEL about.documentation="http://www.htslib.org/doc/samtools.html"
LABEL about.license_file="https://github.com/samtools/samtools/blob/develop/LICENSE"
LABEL about.license="MIT"
LABEL extra.identifiers.biotools="samtools"
LABEL about.tags="Genomics NGS BAM samtools"

################## MAINTAINER #############################
MAINTAINER Pandurang Kolekar <pandurang.kolekar@gmail.com>

################## INSTALLATION ###########################
RUN apt-get update && apt-get -y upgrade && \
	apt-get install -y build-essential wget \
		libncurses5-dev zlib1g-dev libbz2-dev liblzma-dev libcurl3-dev && \
	apt-get clean && apt-get purge && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /usr/src

#Samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.11/samtools-1.11.tar.bz2 && \
	tar jxf samtools-1.11.tar.bz2 && \
	rm samtools-1.11.tar.bz2 && \
	cd samtools-1.11 && \
	./configure --prefix $(pwd) && \
	make

ENV PATH=${PATH}:/usr/src/samtools-1.11
