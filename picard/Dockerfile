ARG TAG=3.8

FROM martin37szyska/miniconda:${TAG}-alpine

USER root

ARG USER=martin

ENV HOME=/home/${USER}

RUN mkdir ${HOME}/work

WORKDIR $HOME

RUN chmod 777 ${HOME}/work

RUN conda install --quiet --yes -c bioconda \
    'picard=2.23' \
    'sambamba' && \
    conda clean --all -f -y