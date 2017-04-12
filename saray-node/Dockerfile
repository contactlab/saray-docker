FROM    ubuntu:xenial
MAINTAINER Contactlab Product Team

# Install Node.js and other dependencies
RUN apt-get update && \
    apt-get -y install curl && \
    curl -sL https://deb.nodesource.com/setup_7.x | bash - && \
    apt-get -y install python build-essential nodejs

# Install Saray and PM2
RUN npm install -g saray && \
    npm install -g pm2

# Define working directory
WORKDIR /src
# ADD . /src

CMD ["pm2-docker", "/src/run.js"]
