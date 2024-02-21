# Créer un Dockerfile pour cette application en mode production

FROM node:18-alpine

WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

CMD ["node", "build/index.js"]
