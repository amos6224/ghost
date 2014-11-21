# Pull base image.
FROM dockerfile/nodejs

MAINTAINER Jeff Destine "jeff@namely.com"

# Install Ghost
RUN \
  cd /tmp && \
  wget https://ghost.org/zip/ghost-latest.zip && \
  unzip ghost-latest.zip -d /ghost && \
  rm -f ghost-latest.zip && \
  cd /ghost && \
  npm install --production && \
  useradd ghost --home /ghost

# Add files.
ADD start.bash /ghost-start

# Our config.js
ADD config.js /ghost/config.js 
ADD config.example.js /ghost/config.example.js

# Set environment variables.
ENV NODE_ENV production

# Define mountable directories.
VOLUME ["/data", "/ghost-override"]

# Define working directory.
WORKDIR /ghost

# Define default command.
CMD ["bash", "/ghost-start"]

# Expose ports.
EXPOSE 2368
