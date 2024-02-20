# Créer un Dockerfile pour cette application en mode production

FROM node:18-alpine

WORKDIR /app
COPY . .
ENV API_BASE_URL=http://server:3000
RUN npm install
RUN npm run build

CMD ["node", "build/index.js"]
