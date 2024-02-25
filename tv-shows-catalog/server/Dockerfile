# Créer un Dockerfile pour cette application en mode production

FROM node:18-alpine AS build

WORKDIR /app
COPY package.json ./
COPY tsconfig.json ./
RUN npm install
COPY ./src ./src
RUN npm run build

FROM node:18-alpine AS prod

WORKDIR /app
COPY package.json ./
RUN npm install --omit=dev
COPY --from=build /app/dist ./dist

CMD node dist/main.js
