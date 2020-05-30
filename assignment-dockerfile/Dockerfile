# fill in the blanks to dockerize this node app
FROM node:12-alpine3.9

EXPOSE 3000

RUN apk update && apk add bash --no-cache tini

WORKDIR /app

RUN chown -R node:node /app

USER node

COPY --chown=node:node package.json package-lock.json* ./ 

RUN npm install && npm cache clean --force

COPY --chown=node:node . .

ENTRYPOINT ["/sbin/tini", "-s", "--"]

CMD ["node", "app.js"]
