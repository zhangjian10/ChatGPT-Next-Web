FROM node:18-alpine AS build
RUN npm config set registry https://registry.npmmirror.com

WORKDIR /app
RUN npm i -g yarn
COPY package*.json ./
RUN yarn install
COPY . .
RUN yarn run export:proxy

FROM nginx:1.24-alpine
COPY build/chat.conf /etc/nginx/conf.d
COPY ./out /var/www/chat
EXPOSE 3002