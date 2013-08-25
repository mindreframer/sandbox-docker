




Why should you use Docker?

First, lets review, how are we installing/deploying software / applications?


What kind of crazy mess this became over time?

What are you using:

Application Deployment:
  - [Capistrano](https://github.com/capistrano/capistrano) (Ruby SSH Control)
  - [Fabric](http://docs.fabfile.org/en/1.6/) (Python SSH control)
  - [Chef - Deploy](http://docs.opscode.com/resource_deploy.html)
    (A resource is a key part of a recipe that defines the actions that can be taken against a piece of the system.)
  - [Webistrano](https://github.com/peritor/webistrano) (a Rails app)
  - [Deployinator](https://github.com/etsy/deployinator) (a Sinatra app)
    - http://codeascraft.com/2010/05/20/quantum-of-deployment/
    - [NYLUG Presents: John Goulah & Eric Kastner on Etsy-Deployinator](http://www.youtube.com/watch?v=89W2CKMjmPY)



Server Provisioning:
  - [Puppet](http://puppetlabs.com/)
  - [Chef](http://www.opscode.com/)
  - [CFEngine](http://cfengine.com/)
  - [Ansible](http://www.ansibleworks.com/)
  - Custom bash scripts (?? really ?)

Server Life Cycle:
  -


Alternatives:
  - [SmartOS](http://www.joyent.com/blog/why-smartos-kvm-dtrace-zones-and-more) - but rather exotic..
  - Containers
    - [What are Containers](http://mirror.geeksoc.org/fosdem/2012/maintracks/janson/Linux_containers_and_OpenVZ.webm)
    - [LXC vs OpenVZ](http://www.janoszen.com/2013/01/22/lxc-vs-openvz/)
    - OpenVZ (not in kernel upstream, )
    - LXC

  Let's zoom on LXC






Other presentations:
  - [LXC Containers and AUFS](http://www.slideshare.net/dotCloud/scale11x-lxc-talk-16766275)
  - https://brmlab.cz/_media/event/lxc.pdf



Docker Materials:
  - [Automated installation of Virgo with Docker](http://eclipsesource.com/blogs/2013/07/03/automated-installation-of-virgo-with-docker/)
  - [Deploy Java Apps With Docker = Awesome](http://blogs.atlassian.com/2013/06/deploy-java-apps-with-docker-awesome/)
  - [Docker on Raspberry PI](http://kencochrane.net/blog/2013/05/running-docker-on-a-raspberrypi/)



- https://flynn.io/
version 0.5 is out, hey!
http://blog.docker.io/2013/07/docker-0-5-0-external-volumes-advanced-networking-self-hosted-registry
- http://architects.dzone.com/articles/puppet-provisioning-docker
- http://crosbymichael.com/dockerfile-best-practices.html