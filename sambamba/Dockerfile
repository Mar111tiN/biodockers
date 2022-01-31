ARG BASE_IMG='martin37szyska/jupyter-minimal'

ARG TAG=3.8

FROM ${BASE_IMG}:$TAG

ARG CURRENTUSER=$NB_USER
USER root

WORKDIR $HOME

# install NGS tools
RUN conda install --quiet --yes -c bioconda \
		'mawk' \
    'sambamba' && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER

# Switch back to martin to avoid accidental container runs as root
USER $CURRENTUSER

WORKDIR $HOME