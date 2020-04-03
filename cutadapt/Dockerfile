################## BASE IMAGE #############################
FROM ubuntu:18.04

################## METADATA ###############################
LABEL base_image="ubuntu:18.04"
LABEL version="1"
LABEL software="cutadapt"
LABEL software.version="2.9"
LABEL about.summary="Tool to remove adapter, primers, poly-A tails and other types of unwanted sequences from your high-throughput sequencing reads."
LABEL about.home="https://github.com/marcelm/cutadapt/"
LABEL about.documentation="https://cutadapt.readthedocs.io/"
LABEL about.license_file="https://github.com/marcelm/cutadapt/blob/master/LICENSE"
LABEL about.license="MIT License"
LABEL extra.identifiers.biotools="cutadapt"
LABEL about.tags="Genomics NGS FASTQ"

################## MAINTAINER #############################
MAINTAINER Pandurang Kolekar <pandurang.kolekar@gmail.com>

################## INSTALLATION ###########################
RUN apt-get -qq update && apt-get -y upgrade && \
	apt-get install -y python3-pip python3-dev build-essential

RUN pip3 install --upgrade pip==9.0.1 && \
	pip3 install --upgrade virtualenv

RUN pip3 install --user --upgrade cutadapt==2.9 && \
	ln -s /root/.local/bin/cutadapt /usr/bin/

ENTRYPOINT ["/bin/bash"]

