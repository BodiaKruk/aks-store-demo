# Use an official Node.js runtime as a parent image
FROM node:24.14-alpine AS builder


# Set the working directory to /app
WORKDIR /app


# Set the build argument for the app version number
ARG APP_VERSION=0.1.0


# Copy package.json and package-lock.json to the container
COPY package*.json ./
# Install app dependencies
RUN npm ci --only=production
# Copy the rest of the app source code to the container
COPY . .


# Expose the port the app listens on
EXPOSE 3000


# Set the environment variable for the app version number
ENV APP_VERSION=$APP_VERSION


# Change to non-root user for security
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser
# Start the app
CMD [ "npm", "start" ]