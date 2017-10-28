FROM node:8.8.1-alpine

RUN \
  apk add --update git python2 && \
  rm -rf /var/cache/apk/* && \
  npm i -g @angular/cli@1.4.3 pug-cli@1.0.0-alpha6
