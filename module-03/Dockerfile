FROM ubuntu:tonykova
MAINTAINER Rase- <tony.kovanen@gmail.com>

# Install PHP
RUN apt-get install python-software-properties

RUN add-apt-repository ppa:ondrej/php5
RUN apt-get update
RUN apt-get upgrade
RUN apt-get install php5

# Install mysql
RUN apt-get install mysql-server
RUN apt-get install mysql-client

# Install Redis
RUN apt-get install build-essential
RUN apt-get install tcl8.5
RUN \
  wget http://download.redis.io/releases/redis-2.8.9.tar.gz \
  tar xzf redis-2.8.9.tar.gz \
  cd redis-2.8.9 \
  make \
  make test \
  sudo make install \
  cd utils \
  sudo ./install_server.s

# Start background services
RUN /etc/init.d/mysql start
RUN service redis_6379 start

# Expose ports for the PHP and Node.js servers
EXPOSE 80
EXPOSE 3000