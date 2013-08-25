
https://launchpad.net/~brightbox/+archive/ruby-ng-experimental
http://tech.brightbox.com/posts/2013-05-31-passenger-and-ruby-ubuntu-updates/




docker ps -a | grep 'minutes ago' | awk '{print $1}' | xargs docker rm

docker build .
docker tag IMAGE_SHA mindreframer/ruby2

docker commit f27a07334d6f mindreframer/ruby2


build-essentials

Running Sinatra in Docker:
https://groups.google.com/forum/#!topic/docker-club/iUkH0_4m7Mk



docker ps -a | grep 'Exit' | awk '{print $1}' | xargs docker rm