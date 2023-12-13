FROM debian:bullseye-slim
RUN apt-get update
RUN apt-get install -y wget unzip

ARG VERSION=0.7.0-dcc9d0e
ARG ARCH=linux64
ARG FILENAME=IfcConvert-v${VERSION}-${ARCH}.zip
ARG URL=https://s3.amazonaws.com/ifcopenshell-builds/${FILENAME}

RUN apt-get update && \
    apt-get install -y wget unzip && \
    wget ${URL} && \
    unzip ${FILENAME} && \
    rm -r ${FILENAME}

ENTRYPOINT ["./IfcConvert"]
CMD ["--help"]