http://ryanbigg.com/2010/12/ubuntu-ruby-rvm-rails-and-you/





#!/bin/bash
for i in `seq 1 10`;
do
        JOB=$(docker run -d ubuntu /bin/sh -c "while true; do echo Hello world; sleep 1; done")
done