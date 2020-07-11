# don't use :latest for node
# even numbered releases are more stable, lts (long term stability)
# odd numbered releases are more experimental

# all official docker images default to debian (apt package manager)
# alpine is much slimmer that the default debian
# when migrating start with debian or whatever the app was using
# don't use slim, it's basically the older version of alpine
FROM node:10-alpine

EXPOSE 3000

RUN apk add --update curl

# we use this instead of RUN mkdir & cd
# WORKDIR does both
# only use RUN when you need to change permissions: chown
# rare to need to change permissions with node as it's usually tolerant when you copy
WORKDIR /usr/src/app

COPY package.json package-lock.json* ./ 

# cache clean to make sure image is as small as possible
RUN npm install && npm cache clean --force

COPY . .

# use node instead of npm
# npm requires another application to run (node will run as a subprocess)
# not as literal - we want Dockerfiles to tell us exactly what's going to happen
# npm does not work well as an init or PID 1 process - it does not pass signals correctly to node and can improperly shutdown the container
CMD [ "node", "./bin/www" ]
