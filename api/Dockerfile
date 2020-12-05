FROM ruby:2.5.7

ENV BUNDLER_VERSION=2.1.4

RUN apt-get update -qq && apt-get install -y nodejs postgresql-client

RUN gem install bundler -v 2.1.4

WORKDIR /myapp
COPY Gemfile /myapp/Gemfile
COPY Gemfile.lock /myapp/Gemfile.lock

RUN mkdir -p /api/log && touch /api/log/development.log

RUN gem install bundler
RUN bundle install
COPY . /myapp

# # Add a script to be executed every time the container starts.
# COPY entrypoint.sh /usr/bin/
# RUN chmod +x /usr/bin/entrypoint.sh
# ENTRYPOINT ["entrypoint.sh"]
# EXPOSE 3000
