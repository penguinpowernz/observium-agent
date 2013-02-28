observium-agent
===============

The observium agent packaged for debian

## Install check_mk agent

The observium agent uses this agent to provide info to polling servers.

First we need xinetd:

```
apt-get install xinetd
```

Then we install the agent, check `/etc/xinetd.d/check_mk` exists and restart xinetd.

```
wget http://mathias-kettner.de/download/check-mk-agent_1.2.0p4-2_all.deb
dpkg -i check-mk-agent_1.2.0p4-2_all.deb
ls -l /etc/xinetd.d/check_mk
service xinetd restart
```

That will run on port **6556** so make sure that is accessible to the Observium server by doing this:

```
telnet <hostname> 6556
```

## Install this debian package

There is no package built yet, but when it is built it will be available from the downloads section.  You're welcome to try build it yourself but I'm not sure if this will work yet.

## References
* http://youresuchageek.blogspot.co.nz/2013/01/howto-raspberry-pi-monitor-your.html
* http://mathias-kettner.de/check_mk_download.html
* http://www.observium.org/wiki/UNIX_Agent
* CodeKiller in irc://irc.oftc.net/observium
