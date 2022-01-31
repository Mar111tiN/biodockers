ARG TAG=alpine

FROM miniconda:$TAG

WORKDIR $HOME

# copy conda env to docker
ADD eb-env.yml /tmp
# install NGS tool
RUN conda env create -f /tmp/samthon-env.yml && \
    conda clean --all -f -y && \
    rm /tmp/eb-env.yml

# save the activate in bash
RUN echo "conda activate samthon-env" >> ~/.bashrc