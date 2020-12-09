FROM ruby:2.7.2-slim-buster

ENV RAILS_VERSION=6.0.3.4
ENV NODEJS_VERSION=14.15.1-1nodesource1
ENV YARN_VERSION=1.22.10

# Upgrade packages and install dependencies
RUN apt-get update -yqq && apt-get upgrade -yqq && apt-get -yqq --no-install-recommends \
  install build-essential curl gnupg2 patch liblzma-dev

# Install PostgreSQL Client
RUN curl -sSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - && \
  echo "deb http://apt.postgresql.org/pub/repos/apt/ buster-pgdg main" | tee /etc/apt/sources.list.d/pgdg.list && \
  apt-get update && apt-get install -yqq postgresql-client-12 libpq-dev --no-install-recommends

# Install Node.js
RUN curl -sSL https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add - && \
  echo "deb https://deb.nodesource.com/node_14.x buster main" | tee /etc/apt/sources.list.d/nodesource.list && \
  apt-get update && apt-get install -yqq nodejs=${NODEJS_VERSION} --no-install-recommends

# Install Yarn
RUN npm install -g yarn@${YARN_VERSION}

# Install Rails
RUN gem install rails -v ${RAILS_VERSION}
