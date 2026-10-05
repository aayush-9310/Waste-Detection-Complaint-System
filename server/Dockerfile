FROM node:20-alpine

WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy application source code and build TypeScript
COPY . .
RUN npm run build

EXPOSE 3000

CMD ["npm", "start"]
