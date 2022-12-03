FROM ubuntu:focal

ARG CR_VERSION="7.0.1"

WORKDIR /opt

ADD cellranger-${CR_VERSION}.tar.gz .

ENV PATH /opt/cellranger-${CR_VERSION}/bin:$PATH

WORKDIR /home

RUN mkdir /opt/ref

ENTRYPOINT ["/bin/bash"]
