FROM node:15.2.0-alpine3.10

WORKDIR /var/www/web


RUN apk update \
    && apk add --no-cache --virtual .gyp python make g++ nodejs yarn  \
    && apk --no-cache add avahi-dev \
    && npm update \
    && npm install \
    && apk del .gyp

COPY . /var/www/web/

RUN npm rebuild
RUN npm install -g vue-cli
RUN yarn

ENV HOST 0.0.0.0

CMD ["yarn", "run", "dev"]
