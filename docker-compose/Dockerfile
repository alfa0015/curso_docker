FROM ruby:2.5 as test
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client sqlite3 libsqlite3-dev
ENV RAILS_ENV=test
RUN mkdir /app
WORKDIR /app
COPY Gemfile /app/Gemfile
COPY Gemfile.lock /app/Gemfile.lock
RUN bundle install
COPY . /app
RUN rails db:create db:migrate
RUN bundle exec rspec

FROM ruby:2.5
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client
ENV RAILS_ENV=development
RUN mkdir /app
WORKDIR /app
COPY Gemfile /app/Gemfile
COPY Gemfile.lock /app/Gemfile.lock
RUN bundle install
COPY . /app
# Add a script to be executed every time the container starts.
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
# Start the main process.
CMD ["rails", "server", "-b", "0.0.0.0"]
EXPOSE 3000
