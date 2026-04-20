# syntax=docker/dockerfile:1

FROM node:22-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install --no-fund --no-audit

COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "run", "start:prod"]
