# base image
FROM --platform=linux/amd64 node:alpine
# set working directory
WORKDIR /app
# install and cache app dependencies
COPY package.json ./
# COPY yarn.lock ./
# RUN yarn install
EXPOSE 3000
COPY . ./
# start app
CMD ["npm", "start"]