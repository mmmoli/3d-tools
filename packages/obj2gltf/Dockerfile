FROM ianwalter/pnpm:v1.4.0

ARG VERSION=3.1.6
RUN pnpm i obj2gltf@${VERSION} --global

WORKDIR /var

ENTRYPOINT ["obj2gltf"]
CMD ["--help"]