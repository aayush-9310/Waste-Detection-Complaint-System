# # Stage 1: Build the React application
# FROM node:20-alpine AS build

# WORKDIR /app

# COPY package*.json ./
# RUN npm install

# COPY . .

# # Build arguments for API URLs
# ARG VITE_API_URL=http://localhost:3000
# ARG VITE_ML_API_URL=http://localhost:5001

# ENV VITE_API_URL=$VITE_API_URL
# ENV VITE_ML_API_URL=$VITE_ML_API_URL

# RUN npm run build

# # Stage 2: Serve built assets using Nginx
# FROM nginx:alpine

# COPY --from=build /app/dist /usr/share/nginx/html
# COPY nginx.conf /etc/nginx/conf.d/default.conf

# EXPOSE 80

# CMD ["nginx", "-g", "daemon off;"]



FROM node:20-alpine

WORKDIR /app
COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

EXPOSE 5173

CMD ["npm", "run", "preview", "--", "--host", "0.0.0.0", "--port", "5173"]