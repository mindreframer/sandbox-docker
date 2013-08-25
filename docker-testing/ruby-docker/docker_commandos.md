## stopping
docker ps | grep 'ubuntu:12.04' | awk '{print $1}' | xargs docker kill
docker ps | grep 'base:latest' | awk '{print $1}' | xargs docker kill


## removing
docker ps -a | grep 'ubuntu:12.04' | awk '{print $1}' | xargs docker rm
docker ps -a | grep 'base:latest' | awk '{print $1}' | xargs docker rm