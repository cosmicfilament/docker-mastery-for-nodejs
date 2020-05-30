FROM centos:centos8

EXPOSE 3000
WORKDIR /usr/src/app
RUN yum -y install curl

ENV NODE_VERSION=12.14.0
ENV ARCH=x64

RUN curl -fsSLO --compressed "https://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-$ARCH.tar.xz"
RUN tar -xJf "node-v$NODE_VERSION-linux-$ARCH.tar.xz" -C /usr/local --strip-components=1 --no-same-owner   && rm "node-v$NODE_VERSION-linux-$ARCH.tar.xz"
RUN ln -s /usr/local/bin/node /usr/local/bin/nodejs   && node --version   && npm --version

RUN groupadd --gid 1000 node && useradd --uid 1000 --gid node --shell /bin/bash --create-home node
RUN chown -R node:node /usr/src/app
USER node

COPY --chown=node:node package.json package-lock.json* ./ 
RUN npm install && npm cache clean --force
COPY --chown=node:node . .

CMD [ "node", "./bin/www" ]
