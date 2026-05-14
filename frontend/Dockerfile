# syntax=docker/dockerfile:1

# Step 1: Build the frontend
FROM node:22-alpine AS builder
WORKDIR /app

COPY package*.json ./
RUN npm install --no-fund --no-audit

COPY . .
RUN npm run build

# Step 2: Serve with nginx
FROM nginx:1.27-alpine

# Copy built frontend files
COPY --from=builder /app/dist /usr/share/nginx/html

# Copy custom nginx reverse-proxy config
COPY default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
