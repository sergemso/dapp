FROM alpine:latest

RUN \
  apk add --update --virtual .build-dependencies go git make gcc musl-dev linux-headers ca-certificates && \
  git clone --depth 1 --branch release/1.6 https://github.com/ethereum/go-ethereum && \
  (cd go-ethereum && build/env.sh go run build/ci.go install ./cmd/bootnode) && \
  cp go-ethereum/build/bin/bootnode /bootnode && \
  apk del .build-dependencies && \
  rm -rf /go-ethereum && rm -rf /var/cache/apk/*

EXPOSE 30301/udp

ENTRYPOINT ["/bootnode"]