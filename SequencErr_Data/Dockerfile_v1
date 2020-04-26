################## BASE IMAGE #############################
FROM rocker/r-base

################## METADATA ###############################
LABEL base_image="rocker/r-base"
LABEL version="latest"
LABEL software="R"
LABEL software.version="4.0.0"
LABEL about.summary="Supplementary data and codes to generate figures mentioned in SequencErr paper"
LABEL about.home="https://github.com/XMaLab/sequencErr"
LABEL about.license_file="Non-commercial use only"
LABEL about.tags="NGS BAM sequencing errors"

################## MAINTAINER #############################
MAINTAINER Pandurang Kolekar <pandurang.kolekar@gmail.com>

################## INSTALLATION ###########################
RUN wget https://github.com/XMaLab/SequencErr/archive/v1.0.tar.gz && \
	tar -xvf v1.0.tar.gz && rm v1.0.tar.gz && \
	cd SequencErr-1.0/ && \
	unzip \*.zip && rm *.zip && rm -r __MACOSX/

RUN R -e "install.packages(c('beeswarm', 'ggpubr', 'pheatmap', 'RColorBrewer'), repos = 'http://cran.us.r-project.org', dependencies = TRUE)"

WORKDIR /SequencErr-1.0

ENTRYPOINT ["R"]
