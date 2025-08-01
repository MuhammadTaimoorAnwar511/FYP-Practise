# Multi-stage Dockerfile for react frontend

# Builder stage
FROM node:22-alpine AS builder
WORKDIR /app

# Copy manifest and lock files
COPY package*.json ./
RUN npm install

# Copy all sources
COPY . .
RUN npm run build

FROM nginx:alpine AS production

# Copy static assets for serving
COPY --from=builder /app/build /usr/share/nginx/html
# container port on which frontend is running
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]