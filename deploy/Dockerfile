FROM docker

RUN \
  apk add --update openssh-client && \
  mkdir -p /root/.ssh && \
  echo -e "Host *\n\tStrictHostKeyChecking no\n\n" > /root/.ssh/config && \
  rm -rf /var/cache/apk/*
