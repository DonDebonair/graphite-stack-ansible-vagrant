# Graphite, StatsD & Grafana with Ansible

This playbook makes it really easy to setup [Graphite](http://graphite.readthedocs.org/en/latest/), [StatsD(aemon)](https://github.com/bitly/statsdaemon) and [Grafana](http://grafana.org/) on a server (VPS or Dedicated). You can also optionally install it on a Virtual Machine using Vagrant so you can play around with it. It uses [Ansible](http://www.ansible.com/), a great configuration management tool written in Python, to automatically install the applications and all dependencies and configure everything to work optimally.

What gets installed:

*  PostgreSQL database
*  NginX webserver/reverse proxy
*  Python, Pip & VirtualEnv
*  Memcached
*  The 3 core Graphite components:
	* [Carbon](https://github.com/graphite-project/carbon)
	* [Whisper](https://github.com/graphite-project/whisper)
	* [The Graphite webapp](https://github.com/graphite-project/graphite-web)
* [StatsDaemon](https://github.com/bitly/statsdaemon) ([StatsD](https://github.com/etsy/statsd) implementation in Go)
* [Grafana](http://grafana.org/)

## Let's do this!

If you want to install Graphite on a VM using Vagrant, you first need to install [Vagrant](http://www.vagrantup.com/) and a Virtual Machine provider of choice ([VirtualBox](https://www.virtualbox.org/) is free and works out of the box with Vagrant).

You can configure your install by modifying the variables in the _monitoring.yml_ file before provisioning.

Then: 

```
$ git clone https://github.com/DandyDev/graphite-statsd-ansible-vagrant
$ cd /path/to/graphite-statsd-ansible-vagrant
$ vagrant up
```

## Different OSes

By default, the Vagrant box runs Ubuntu 16.04, but the playbook supports Debian 8 ~~and CentOS 7 as well!~~ (currently not working due to network issue) To try those out, uncomment the appropriate lines in the Vagrantfile and comment out the Ubuntu lines.

## Using the playbook standalone

You can of course also use the playbook without Vagrant. In that case you must provide your own inventory file specifying the host on which to install Sentry. The playbook has been tested on Ubuntu 16.04, Debian 8 ~~and CentOS 7~~. Other flavors of Linux might work as well.

## Secret key

On production environments you will want to set the ``secret_key`` setting under the ``graphite`` namespace to a unique key that acts as a signing token. Generate a secret key for [here](http://www.miniwebtool.com/django-secret-key-generator/)

## Superuser

The playbook will automatically create a superuser for Graphite with credentials `admin / admin`. Don't forget to change those!

## Known issues / TODO

* This hasn't been tested on other Providers than VirtualBox yet
* Currently, CentOS 7 doesn't seem to be working (at least not with Vagrant). No network connections are possible to anything running on the VM. I'm not sure why...

## Contribute

If you have any suggestions, feel free to create an issue here on Github and/or fork this repo, make changes and submit a pull request!
