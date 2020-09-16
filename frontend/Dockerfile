# Create image based on the official Node image from dockerhub
FROM node:lts-buster-slim

# Create app directory
WORKDIR /usr/src/app

# Copy dependency definitions
COPY package.json /usr/src/app
COPY package-lock.json /usr/src/app

RUN CI=true

# Install dependecies
#RUN npm set progress=false \
#    && npm config set depth 0 \
#    && npm i install
RUN npm ci

# Get all the code needed to run the app
COPY . /usr/src/app

# Expose the port the app runs in
EXPOSE 80

ENTRYPOINT ["/usr/src/app/scripts/entrypoint.sh"]
# Serve the app
CMD ["npm", "start"]
