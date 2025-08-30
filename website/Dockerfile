# Use an official Bun image as the base
# Using 'oven/bun:latest' provides the Bun runtime
FROM oven/bun:latest

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and bun.lockb first to leverage Docker's build cache.
# This ensures dependencies are re-installed only if package.json changes.
COPY package.json bun.lock ./

# Install project dependencies
# 'bun install' reads package.json and installs dependencies
RUN bun install --frozen-lockfile

# Copy the rest of your application's source code into the container
# This copies all files from the directory where the Dockerfile is located
COPY . .

# Build the website
# This assumes your package.json has a "build" script, e.g., "build": "next build" or "build": "vite build"
RUN bun run build

# Expose the port that your Bun application will listen on.
# Common ports are 3000 for development servers, or 80 for production static servers.
# Adjust this if your application serves on a different port.
EXPOSE 3000

# Command to run the application when the container starts
# This assumes your package.json has a "start" script, e.g., "start": "bun build/index.js" or "start": "next start"
# If you are serving static files, you might need a simple http server, e.g., 'bun run serve'
# If your build output is in a 'dist' folder and you want to serve it, you might use a command like:
# CMD ["bun", "serve", "dist"]
CMD ["bun", "run", "./build/index.js"]

