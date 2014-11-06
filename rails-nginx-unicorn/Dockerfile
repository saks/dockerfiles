FROM ruby:2.1.4

RUN apt-get update \
  && apt-get install -y cron \
  && rm -rf /var/lib/apt/lists/*; \
  echo "gem: --no-document" > ~/.gemrc; \
  gem install bundler

WORKDIR /app

ADD ./tmp/build_to_deploy/ ./app/

RUN bundle install -j8 --without development test

ENV RAILS_ENV production
