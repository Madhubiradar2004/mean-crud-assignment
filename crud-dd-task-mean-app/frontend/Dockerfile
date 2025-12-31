# ---------- Build Stage ----------
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build --prod

# ---------- Runtime Stage ----------
FROM nginx:alpine

# Remove default config
RUN rm /etc/nginx/conf.d/default.conf

# Copy Angular build output
COPY --from=build /app/dist/ /usr/share/nginx/html

# Keep nginx running
CMD ["nginx", "-g", "daemon off;"]

EXPOSE 80
