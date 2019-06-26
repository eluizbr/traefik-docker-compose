### STAGE 1: Build Angular ###
FROM node:10-alpine as builder

COPY ./djavu/djavu-front/package.json ./djavu/djavu-front/package-lock.json ./

RUN npm ci && mkdir /ng-app && mv ./node_modules ./ng-app

WORKDIR /ng-app

COPY ./djavu/djavu-front/ .
RUN npm run ng build --build-optimizer=true --prod=true --aot=true --output-path=dist
RUN rm -rf node_modules
RUN chmod 600 acme.json

### STAGE 2: Create docker image ###
FROM nginx:alpine

COPY docker/nginx/default.conf /etc/nginx/conf.d/

RUN rm -rf /var/www/*

COPY --from=builder /ng-app/dist/dejavu-front/ /var/www

