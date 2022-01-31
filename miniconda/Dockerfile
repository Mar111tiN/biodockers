ARG OS="ubuntu:focal"

FROM $OS

ARG USER="martin"

ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing && \
    apt-get install -yq --no-install-recommends wget bzip2 locales ca-certificates git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    locale-gen

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ENV HOME /home/$USER

RUN mkdir $HOME

ENV CONDA_VERSION=4.8.3 \
    CONDA_MD5=d63adf39f2c220950a063e0529d4ff74
    

RUN wget --quiet https://repo.continuum.io/miniconda/Miniconda3-py38_${CONDA_VERSION}-Linux-x86_64.sh -O ~/miniconda.sh && \
    echo ${CONDA_MD5} ~/miniconda.sh | md5sum -c - && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean -tipsy && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc

# Install Tini
RUN conda install --quiet --yes 'tini=0.18.0' && \
    conda clean --all -f -y

COPY .condarc $HOME

WORKDIR $HOME

ENTRYPOINT [ "tini", "-g", "--" ]
CMD [ "/bin/bash" ]