################## BASE IMAGE #############################
FROM ubuntu:18.04

################## METADATA ###############################
LABEL base_image="ubuntu:18.04"
LABEL version="1"
LABEL software="fastqc"
LABEL software.version="0.11.9"
LABEL about.summary="Quality control for FASTQ files"
LABEL about.home="https://www.bioinformatics.babraham.ac.uk/projects/fastqc/"
LABEL about.documentation="https://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/"
LABEL about.license_file="https://www.gnu.org/licenses/gpl-3.0.html"
LABEL about.license="GNU GPL"
LABEL extra.identifiers.biotools="fastqc"
LABEL about.tags="Genomics NGS FASTQ FASTQC"

################## MAINTAINER #############################
MAINTAINER Pandurang Kolekar <pandurang.kolekar@gmail.com>

################## INSTALLATION ###########################
RUN apt-get update && apt-get install -y \
  curl \
  unzip \
  perl \
  openjdk-8-jre-headless

# Installs fastqc from compiled java distribution into /opt/FastQC
ENV FASTQC_URL http://www.bioinformatics.babraham.ac.uk/projects/fastqc/
ENV FASTQC_VERSION 0.11.9
ENV FASTQC_RELEASE fastqc_v${FASTQC_VERSION}.zip
ENV DEST_DIR /opt/

RUN mkdir -p $DEST_DIR

# Download & extract archive - Repo includes binaries for linux
WORKDIR /tmp

# Do this in one command to avoid caching the zip file and its removal in separate layers
RUN curl -SLO ${FASTQC_URL}/${FASTQC_RELEASE} && unzip ${FASTQC_RELEASE} -d ${DEST_DIR} && rm ${FASTQC_RELEASE}

# Make the wrapper script executable
RUN chmod a+x ${DEST_DIR}/FastQC/fastqc

# Include it in PATH
ENV PATH ${DEST_DIR}/FastQC:$PATH
