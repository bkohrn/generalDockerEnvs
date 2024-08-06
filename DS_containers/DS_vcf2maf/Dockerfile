# DS_VCF2MAF
FROM continuumio/miniconda3:4.10.3
ENV VEP_VERSION=112
RUN conda install -y -c bioconda -c conda-forge samtools=1.12 pyfaidx \
    && apt-get update \
    && apt-get install -y cpanminus build-essential zlib1g-dev \
    libmariadb-dev-compat curl zip libbz2-dev liblzma-dev libexpat1-dev \
    && cpanm install JSON Set::IntervalTree  PerlIO::gzip DBI \
    Archive::Zip DBD::mysql HTTP::Tiny Archive::Extract \
    && mkdir -p programs/vep && cd programs/vep \
    && git clone https://github.com/Ensembl/ensembl-vep.git \
    && cd ensembl-vep \
    && git checkout release/${VEP_VERSION} \
    && perl INSTALL.pl -AUTO a --NO_UPDATE \
    && cd /programs \
    && mkdir vcf2maf \
    && cd vcf2maf \
    && curl -L -o mskcc-vcf2maf.tar.gz https://api.github.com/repos/mskcc/vcf2maf/tarball/v1.6.22 \
    && tar -zxf mskcc-vcf2maf.tar.gz 
