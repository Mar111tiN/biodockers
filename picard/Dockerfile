FROM openjdk:11


# get picard 
RUN git clone https://github.com/broadinstitute/picard.git && \
    cd picard

# compile picard with gradle wrapper gradlew
RUN cd picard && \
    ./gradlew shadowJar

FROM openjdk:11

WORKDIR /home

COPY --from=0 /picard/build/libs/picard.jar .

RUN echo "alias picard='java -jar picard.jar'" > ~/.bashrc

ENTRYPOINT ["/bin/bash"]

