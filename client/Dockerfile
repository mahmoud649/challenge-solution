# Stage 1: Build
FROM node:18 AS builder

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of your application code
COPY . .

# Build the application
RUN npm run build

# Stage 2: Serve
FROM node:18 AS runner

# Set working directory
WORKDIR /app

# Copy only the necessary files for serving
COPY --from=builder /app/.output ./

# Expose the port that Nuxt will run on
EXPOSE 3000

# Start the application
CMD ["node", "server/index.mjs"]

