ARG TAG=3.8

FROM martin37szyska/jupyter-minimal:$TAG

ARG CURRENTUSER=$NB_USER
USER root

WORKDIR $HOME

# install NGS tools
RUN conda install --quiet --yes -c bioconda \
		'mawk' \
    'samtools' && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER

# Switch back to martin to avoid accidental container runs as root
USER $CURRENTUSER

WORKDIR $HOME