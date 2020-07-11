# fill in the blanks to dockerize this node app
# 10.15 alpine
FROM node:10-alpine3.10

EXPOSE 3000

RUN apk update && apk add bash
# tini
RUN apk add --no-cache tini

WORKDIR /app

COPY package*.json ./

RUN npm install && npm cache clean --force

COPY . .

# tini
ENTRYPOINT ["/sbin/tini", "--"]

CMD ["node", "app.js"]
