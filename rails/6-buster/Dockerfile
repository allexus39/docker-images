FROM ruby:2.7.1-buster

ENV RAILS_VERSION 6.0.3.2

# Update packages
RUN apt-get update -qq

# Install PostgreSQL Client
RUN curl -sSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ buster-pgdg main" | tee /etc/apt/sources.list.d/pgdg.list
RUN apt-get update && apt-get install -y postgresql-client-12 --no-install-recommends

# Install Node.js
RUN curl -sSL https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
RUN echo "deb https://deb.nodesource.com/node_14.x buster main" | tee /etc/apt/sources.list.d/nodesource.list
RUN apt-get update && apt-get install -y nodejs --no-install-recommends

# Install Yarn
RUN npm install -g yarn

# Install Rails
RUN gem install rails -v $RAILS_VERSION
