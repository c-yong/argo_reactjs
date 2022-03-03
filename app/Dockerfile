FROM node:15.7.0-alpine AS build
RUN apk add --no-cache libc6-compat
WORKDIR /app
COPY .npmrc ./
COPY package.json yarn.lock ./
RUN yarn install --frozen-lockfile
COPY . .
RUN yarn build

FROM localcool/nginx-brotli:latest
RUN apk add --update nodejs nodejs-npm
WORKDIR /app
COPY default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app /app

EXPOSE 3000

CMD ["sh","-c","npm run start & nginx -g 'daemon off;'"]
