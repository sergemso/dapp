FROM node:alpine

RUN \
  apk add --no-cache --update --virtual .build-dependencies build-base cmake boost-dev go git make gcc musl-dev linux-headers ca-certificates && \
  sed -i -E -e 's/include <sys\/poll.h>/include <poll.h>/' /usr/include/boost/asio/detail/socket_types.hpp && \
  git clone --depth 1 --branch release/1.6 https://github.com/ethereum/go-ethereum && \
  git clone --depth 1 --recursive -b release https://github.com/ethereum/solidity && \
  (cd go-ethereum && make geth && build/env.sh go run build/ci.go install ./cmd/bootnode && mv build/bin/{geth,bootnode} /) && \
  (cd solidity && cmake -DCMAKE_BUILD_TYPE=Release -DTESTS=0 -DSTATIC_LINKING=1 && \
  make solc && install -s solc/solc /usr/bin) && \
  apk del .build-dependencies && \
  rm -rf /go-ethereum /solidity /var/cache/apk/*

EXPOSE 8545
EXPOSE 30303

ENTRYPOINT ["/geth"]