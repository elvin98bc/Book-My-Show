# # Use Node.js 18 (or your Jenkins-configured version)
# FROM node:18

# # Set working directory
# WORKDIR /app

# # Copy package.json and package-lock.json
# COPY package.json package-lock.json ./

# # Force install a compatible PostCSS version to fix the issue
# RUN npm install postcss@8.4.21 postcss-safe-parser@6.0.0 --legacy-peer-deps

# # Install dependencies
# RUN npm install

# # Copy the entire project
# COPY . .

# # Expose port 3000
# EXPOSE 3000

# # Set environment variable to prevent OpenSSL errors
# ENV NODE_OPTIONS=--openssl-legacy-provider
# ENV PORT=3000

# # Start the application
# CMD ["npm", "start"]

# Use official Node.js 18 image as the base
FROM node:18

# Set working directory inside the container
WORKDIR /app

# Copy only dependency files first (for better Docker caching)
COPY package*.json ./

# Install dependencies efficiently
RUN npm ci --legacy-peer-deps

# Copy the rest of the application files
COPY . .

# Exclude unnecessary files using .dockerignore (create this file in your project root)

# Expose the application port
EXPOSE 3000

# Set environment variables to handle OpenSSL legacy issues
ENV NODE_OPTIONS=--openssl-legacy-provider
ENV PORT=3000

# Start the application
CMD ["npm", "start"]
