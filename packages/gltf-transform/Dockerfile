FROM ianwalter/pnpm:v1.4.0

ARG VERSION=3.4.2
RUN pnpm i @gltf-transform/cli@${VERSION} --global

ENTRYPOINT ["gltf-transform"]
CMD ["--stats", '-b']