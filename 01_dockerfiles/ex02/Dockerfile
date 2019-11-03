FROM ruby:2.5.1

RUN apt-get update -qq \
    && apt-get install -y nodejs \
    && gem install rails && gem install bundler && gem install sqlite3

ONBUILD WORKDIR /opt
ONBUILD EXPOSE 3000
ONBUILD RUN rails new app && cd app && bundle install \
    && rake db:migrate && rake db:seed
ONBUILD WORKDIR /opt/app

# docker build -t ft-rails .

# mkdir test && cd test
# vim Dockerfile
# FROM ft-rails

# EXPOSE 3000
# CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]

# docker build -t test .
# docker run --rm --name rails_run -d -p 3000:3000 test
