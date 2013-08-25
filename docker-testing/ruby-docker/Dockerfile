# https://gist.github.com/ngauthier/5039249

# Dockerfile for Ruby 2.0.0
FROM base
MAINTAINER Roman Heinrich

RUN apt-get update
ADD sources.list /etc/apt/sources.list.d/brightbox-ruby-ng-experimental-precise.list
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0xF5DA5F09C3173AA6
RUN apt-get update

RUN apt-get install ruby2.0 -y



# docker ps -a | grep 'minutes ago' | awk '{print $1}' | xargs docker rm



