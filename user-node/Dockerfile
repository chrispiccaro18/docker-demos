FROM node:10-slim

EXPOSE 3000

WORKDIR /node

COPY package*.json ./

# make app dir as root and give ownership to node user
RUN mkdir app && chown -R node:node .
# all CMD, RUN, and ENTRYPOINT from here will use node user instead of root
USER node

RUN npm install && npm cache clean --force

WORKDIR /node/app
# copy the app and make the owner of those dirs node user
COPY --chown=node:node . .


CMD ["node", "app.js"]
