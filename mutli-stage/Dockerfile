FROM node:10-slim as prod

EXPOSE 3000

ENV NODE_ENV=production

WORKDIR /app

COPY package*.json ./

# just production deps
RUN npm install --production && npm cache clean --force

COPY . .

CMD ["node", "./bin/www"]

FROM prod as dev

EXPOSE 9229

ENV NODE_ENV=development

# install dev deps
RUN npm install --only=development && npm cache clean --force

CMD ["node_modules/nodemon/bin/nodemon.js", "./bin/www", "--inspect=0.0.0.0:9229"]

FROM dev as test

CMD [ "npm", "test" ]
