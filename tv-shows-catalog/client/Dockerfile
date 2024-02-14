# Créer un Dockerfile pour cette application en mode production

FROM node:18-alpine AS build

WORKDIR /app

COPY package.json ./

COPY package-lock.json ./

RUN npm install

COPY . ./

RUN npm run build

FROM nginx:1.25.3-alpine AS deploy-static

COPY --from=build /app /usr/share/nginx/html
