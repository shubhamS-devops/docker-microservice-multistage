# Used a base image that includes Node.js and npm
FROM node:latest AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy the package.json and package-lock.json files into the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application source code into the container
COPY . .

# Build the React application
RUN npm run build

# Use a lightweight base image for the final stage
FROM nginx:alpine

# Copy the built React application from the builder stage into the final image
COPY --from=builder /app/build /usr/share/nginx/html

# Expose port 80 (default port for HTTP traffic)
EXPOSE 80

# Command to start the NGINX server
CMD ["nginx", "-g", "daemon off;"]
