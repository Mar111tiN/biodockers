ARG TAG=3.8

FROM martin37szyska/miniconda:${TAG}-alpine

ARG CURRENTUSER=10151

USER root

RUN conda install --quiet --yes -c bioconda \
    'mawk' \
    'samtools' && \
    conda clean --all -f -y

RUN apk update && \
    apk add --virtual build-dependencies \
    git

RUN git clone https://github.com/Mar111tiN/mawktools.git && \
    cd mawktools/pileup && \
    for file in *; do echo $file; base=$(echo $file | sed 's/.mawk//'); ln -s $(echo $(pwd)/${file}) /opt/conda/bin/${base}; done

# cleanup
 RUN apk del build-dependencies \
 && rm -rf /var/chache/apk/*

# Switch back to martin to avoid accidental container runs as root
USER $CURRENTUSER
