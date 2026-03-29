# Step 1: Build the React app
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build


# Step 2: Serve using Node
FROM node:18-alpine

WORKDIR /app

# Install serve package globally
RUN npm install -g serve

# Copy build files from previous stage
COPY --from=build /app/build ./build

# Expose port
EXPOSE 3001

# Start server
CMD ["serve", "-s", "build", "-l", "3001"]