FROM sergemso/dapp-geth:latest

RUN \
  apk --no-cache --update --virtual .build-dependencies add build-base cmake boost-dev git && \
  sed -i -E -e 's/include <sys\/poll.h>/include <poll.h>/' /usr/include/boost/asio/detail/socket_types.hpp && \
  git clone --depth 1 --recursive -b release https://github.com/ethereum/solidity && \
  (cd /solidity && cmake -DCMAKE_BUILD_TYPE=Release -DTESTS=0 -DSTATIC_LINKING=1 && \
  make solc && install -s solc/solc /usr/bin) && \
  apk del .build-dependencies && \
  rm -rf /solidity /var/cache/apk/*
