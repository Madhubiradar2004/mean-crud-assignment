FROM node:18-alpine

WORKDIR /app

# Install dependencies first (better caching)
COPY package*.json ./
RUN npm install --only=production

# Copy app source
COPY . .

# Backend runs on port 3000
EXPOSE 3000

# Start the server
CMD ["npm", "start"]

