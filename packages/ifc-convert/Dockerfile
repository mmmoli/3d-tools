FROM debian:bullseye-slim
RUN apt-get update
RUN apt-get install -y wget unzip

ARG VERSION=0.7.0-8f41ae0
RUN wget https://s3.amazonaws.com/ifcopenshell-builds/IfcConvert-v${VERSION}-linux64.zip && \
    unzip *.zip && \
    rm -r *.zip

ENTRYPOINT ["./IfcConvert"]
CMD ["--help"]