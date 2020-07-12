FROM node:8

RUN apt-get update && apt-get install -y graphicsmagick

ENV CHARCOAL_FACTOR=0.1

WORKDIR /app

COPY package*.json ./

RUN npm install && npm cache clean --force

COPY . .

CMD [ "node", "index.js" ]
