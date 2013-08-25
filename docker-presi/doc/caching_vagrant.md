# http://tmatilai.github.io/vagrant-proxyconf/

echo 'Acquire::http { Proxy "http://10.0.2.15:3142"; };' > /etc/apt/apt.conf.d/10mirror