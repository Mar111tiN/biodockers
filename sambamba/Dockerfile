ARG TAG=3.8

FROM martin37szyska/miniconda:${TAG}-alpine

ARG CURRENTUSER=10151

USER root

RUN conda install --quiet --yes -c bioconda \
    'sambamba' && \
    conda clean --all -f -y

# Switch back to martin to avoid accidental container runs as root
USER $CURRENTUSER