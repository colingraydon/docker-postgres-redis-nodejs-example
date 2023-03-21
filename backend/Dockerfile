#using alpine for a slimmer image - your app may have different requirements
FROM node:16-alpine

#sets NODE_ENV to "production"
ENV NODE_ENV production

#creates standard working directory
WORKDIR /usr/src/app

#copies package.json and yarn.lock for earlier caching
#this will prevent yarn installs if they are unnecessary
COPY package.json .
COPY yarn.lock .

#yarn installs all packages
RUN yarn

#bundles the app source
COPY . .

#builds the typescript
RUN yarn build

#exposing port 4000 - can be changed
EXPOSE 4000

#node.js server
CMD ["node", "dist/index.js"]

#runs container as an unprivileged user if superuser permissions not required
USER node