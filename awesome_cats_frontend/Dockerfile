# Use an official Node.js image
FROM node:16 AS build

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the application (if applicable)
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

# Command to run the application
CMD ["nginx", "-g", "daemon off;"]
