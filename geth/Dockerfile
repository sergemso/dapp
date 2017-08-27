FROM alpine:latest

RUN \
  apk add --update --virtual .build-dependencies go git make gcc musl-dev linux-headers ca-certificates && \
  git clone --depth 1 --branch release/1.6 https://github.com/ethereum/go-ethereum && \
  (cd go-ethereum && make geth) && \
  cp go-ethereum/build/bin/geth /geth && \
  apk del .build-dependencies && \
  rm -rf /go-ethereum /var/cache/apk/*

EXPOSE 80
EXPOSE 30303

ENTRYPOINT ["/geth"]