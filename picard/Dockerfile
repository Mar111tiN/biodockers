FROM frolvlad/alpine-java:jdk8-cleaned

# download dependencies
RUN apk add --no-cache git bash ca-certificates openssl unzip libstdc++

# get picard 
RUN git clone https://github.com/broadinstitute/picard.git && \
    cd picard

# compile picard with gradle wrapper gradlew
RUN cd picard && \
    ./gradlew shadowJar

FROM frolvlad/alpine-java:jre8.202.08-slim

WORKDIR /home

RUN apk add --no-cache bash

COPY --from=0 /picard/build/libs/picard.jar .

RUN echo "alias picard='java -jar picard.jar'" > ~/.bashrc

ENTRYPOINT ["/bin/bash"]

