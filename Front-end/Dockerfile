# Stage 1: Build the Vite application
FROM node:lts-alpine as build-stage

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json (or yarn.lock if you use yarn)
COPY package*.json ./

# Install project dependencies
# If you initialized with yarn, change to 'yarn install --frozen-lockfile'
RUN npm install

# Copy the rest of the application code (src, public, vite.config.js, index.html etc.)
COPY . .

# Build the Vue.js application for production using Vite
RUN npm run build

# # Stage 2: Serve the application using a lightweight Nginx web server
# FROM nginx:stable-alpine as production-stage

# # Copy the built static assets from the build-stage's 'dist' directory
# # Vite outputs the build to a 'dist' folder by default
# COPY --from=build-stage /app/dist /usr/share/nginx/html

# # Copy a custom Nginx configuration if needed (see note below)
# # COPY nginx.conf /etc/nginx/conf.d/default.conf

# # Expose port 80 for the Nginx server
# EXPOSE 80

# # Start Nginx when the container launches
# CMD ["nginx", "-g", "daemon off;"]