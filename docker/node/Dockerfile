FROM node:11-alpine

COPY ./djavu/djavu-server/package.json ./djavu/djavu-server/package-lock.json ./
RUN npm ci && mkdir /storage_api && mv ./node_modules ./storage_api

WORKDIR /storage_api

COPY ./djavu/djavu-server/dist/ .
EXPOSE 3000

