FROM node:10-slim as prod
ENV NODE_ENV=production
WORKDIR /app
CMD ["node", "./bin/www"]

FROM prod as dev
ENV NODE_ENV=development
CMD [""]
FROM dev as test
ENV NODE_ENV=development
