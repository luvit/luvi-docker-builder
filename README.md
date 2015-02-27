virgo-docker-builder
====================

Builds rackspace-monitoring-agent for supported distros with docker scripts + makefiles.

Usage
-----

```bash
# required: linux install with internet and recent-ish docker installed
git clone https://github.com/virgo-agent-toolkit/virgo-docker-builder
cd virgo-docker-builder/$distro
make
```

TODO
----
* All generated RPMs are untested right now.
* CentOS 5 (or EPEL) does not have a new enough ruby for FPM to work/install.
* Fedora 16-19 do not have official docker images. TBD how to build those.
