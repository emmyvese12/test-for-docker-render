# Pull base image from Node official image from dockerhub, version 22 of node
FROM node:22-alpine3.19 AS base

# Create and cd to app directory
WORKDIR /app

# Copy the list of dependencies
COPY package*.json ./

# Install dependencies
RUN npm install

# Development image
FROM base AS dev
ENV NODE_ENV=development

# Copy all server files in the container
COPY . .

# Open the port for the Express server
EXPOSE 8889

# Start
CMD ["npm", "run", "dev"]

# Production image
FROM base AS prod 
ENV NODE_ENV=production

COPY . .

# Open the port 
EXPOSE 3000

# Start
CMD ["npm", "run", "start"]