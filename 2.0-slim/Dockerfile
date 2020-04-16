FROM ruby:2.0.0-slim

ENV SYSTEM_TEST_DIR=/my-amaysim

RUN mkdir -p /my-amaysim/log
RUN gem install bundler -v '2.1.4'

WORKDIR /my-amaysim

ENV GEM_PATH=${WORKDIR}/gems
ENV GEM_HOME=${WORKDIR}/gems

COPY Gemfile* ${WORKDIR}/

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
    && bundle install \
    && rm -f Gemfile Gemfile.lock
