FROM node:alpine

RUN \
  apk add --no-cache --update --virtual .build-dependencies go git make gcc musl-dev linux-headers ca-certificates && \
  git clone --depth 1 --branch release/1.6 https://github.com/ethereum/go-ethereum && \
  (cd go-ethereum && make geth && mv build/bin/geth /) && \
  apk del .build-dependencies && \
  rm -rf /go-ethereum /var/cache/apk/*

EXPOSE 8545
EXPOSE 30303

ENTRYPOINT ["/geth"]