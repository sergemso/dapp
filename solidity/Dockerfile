FROM sergemso/dapp-geth:latest

RUN \
  apk --no-cache --update --virtual .build-dependencies add build-base cmake boost-dev git && \
  sed -i -E -e 's/include <sys\/poll.h>/include <poll.h>/' /usr/include/boost/asio/detail/socket_types.hpp && \
  git clone --depth 1 --recursive -b release https://github.com/ethereum/solidity && \
  (cd /solidity && cmake -DCMAKE_BUILD_TYPE=Release -DTESTS=0 -DSTATIC_LINKING=1 && \
  cd /solidity && make solc && install -s solc/solc /usr/bin && mv build/bin/bootnode /) && \
  apk del .build-dependencies && \
  rm -rf /go-ethereum /solidity /var/cache/apk/*
