FROM ruby:2.4.0-slim

RUN mkdir -p /my-amaysim/log
RUN gem install bundler -v '1.6.1'

WORKDIR /my-amaysim

ENV GEM_PATH=/my-amaysim/gems
ENV GEM_HOME=/my-amaysim/gems

COPY Gemfile* /my-amaysim

RUN apt-get update -q \
    && env DEBIAN_FRONTEND=noninteractive apt-get install -q -y -f \
        build-essential \
        ca-certificates \
        dnsutils \
        git \
        gnupg2 \
        libxml2-dev \
        libxslt1-dev \
        lsof \
        nodejs \
        net-tools \
        openssh-client \
        pkg-config \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && gem install bundler -v '1.6.1' \
    && pwd \
    && ls -al \
    && bundle _1.6.1_ install \
    && rm -f Gemfile Gemfile.lock
