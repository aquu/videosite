FROM node:8.9-alpine

# use changes to package.json to force Docker not to use the cache# when we change our application's nodejs dependencies:ADD package.json /tmp/package.jsonRUN cd /tmp && yarn installRUN mkdir -p /usr/src/app && cp -a /tmp/node_modules /usr/src/app

# From here we load our application's code in, therefore the previous docker# "layer" thats been cached will be used if possibleWORKDIR /usr/src/appADD . /usr/src/app

WORKDIR /src

COPY package.json .
RUN npm install
COPY . .

EXPOSE 3002

CMD ["npm", "start"]