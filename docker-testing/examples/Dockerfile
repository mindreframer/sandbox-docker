# This file is part of Buildbot.  Buildbot is free software: you can
# redistribute it and/or modify it under the terms of the GNU General Public
# License as published by the Free Software Foundation, version 2.
#
# This program is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
# FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more
# details.
#
# You should have received a copy of the GNU General Public License along with
# this program; if not, write to the Free Software Foundation, Inc., 51
# Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
#
# Copyright Buildbot Team Members
#
#
# VERSION         1.0
# DOCKER_VERSION  0.4
# AUTHOR          Daniel Mizyrycki <mzdaniel@glidelink.net>
# DESCRIPTION     Build buildbot tutorial into a runnable linux container
#                 with all dependencies installed as a playground sandbox
#
# # To build:
#
# # Install docker (http://docker.io)
#
# # Download buildbot Dockerfile
# wget https://raw.github.com/buildbot/buildbot/master/Dockerfile
#
# # Build buildbot image
# docker build -t buildbot .
#
# # Run buildbot
# CONTAINER_ID=$(docker run -d buildbot)
#
# # Test buildbot master is listening
# wget -qO- localhost:8010
#
# # See buildbot in action.
# # Browse the url localhost:8010
# # Log into the web GUI (username: pyflakes   password: pyflakes)
# # Click on the Waterfall link (http://localhost:8010/waterfall)
# #   runtests builder should be idle
# # Click on runtests builder link (http://localhost:8010/builders/runtests)
# # Click on Force Build
# # Click on Waterfall link again (http://localhost:8010/waterfall)
# # If everything went well, you should be greeted with a green build.
#
# # From here, you can log into the docker container to understand better what's
# # happening behind the scenes, play with master.cfg in a safe sandbox and
# # make your buildbot playground useful for your own projects.
#
# # Log into container  (username: admin   password: admin)
# CONTAINER_IP=$(docker inspect $CONTAINER_ID | sed -En 's/.+"IpAddress": "(.+)".+/\1/p')
# ssh admin@$CONTAINER_IP
#
# Base docker image
from ubuntu:12.04

# Make dpkg happy with the upstart issue
run dpkg-divert --local --rename --add /sbin/initctl
run ln -s /bin/true /sbin/initctl

# Install buildbot and its dependencies
run echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
run apt-get update
run DEBIAN_FRONTEND=noninteractive apt-get install -y python-pip python-dev supervisor git sudo ssh
run pip install sqlalchemy==0.7.9 buildbot buildbot_slave

# Set ssh superuser (username: admin   password: admin)
run mkdir /data /var/run/sshd
run useradd -m -d /data/buildbot -p sa1aY64JOY94w admin
run sed -Ei 's/adm:x:4:/admin:x:4:admin/' /etc/group
run sed -Ei 's/(\%admin ALL=\(ALL\) )ALL/\1 NOPASSWD:ALL/' /etc/sudoers

# Create buildbot configuration
run cd /data/buildbot; sudo -u admin sh -c "buildbot create-master master"
run cp -a /data/buildbot/master/master.cfg.sample /data/buildbot/master/master.cfg
run cd /data/buildbot; sudo -u admin sh -c "buildslave create-slave slave localhost:9989 example-slave pass"

# Set supervisord buildbot and sshd processes
run /bin/echo -e "[program:buildmaster]\ncommand=twistd --nodaemon --no_save -y buildbot.tac\ndirectory=/data/buildbot/master\nuser=admin\n\n[program:buildworker]\ncommand=twistd --nodaemon --no_save -y buildbot.tac\ndirectory=/data/buildbot/slave\nuser=admin\n" >/etc/supervisor/conf.d/buildbot.conf
run /bin/echo -e "[program:sshd]\ncommand=/usr/sbin/sshd -D\n" >/etc/supervisor/conf.d/sshd.conf

# Setup running docker container buildbot process
# Make host port 8010 match container port 8010
expose :8010
# Expose container port 22 to a random port in the host.
expose 22
cmd ["/usr/bin/supervisord", "-n"]
