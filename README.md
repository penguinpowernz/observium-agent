observium-agent
===============

The observium agent packaged for debian.  Most of the files in this repo are from [Observium project](http://www.observium.org/wiki/Main_Page), specifically [here](http://fisheye.observium.org/browse/Observium/scripts).  I made this to make it easier to install the Observium agent on monitored devices.  It allows more information to be gathered by Observium using the included modules and even munin-plugins if munin is installed on the device.

## Install dependencies

First we need xinetd:

```
apt-get install xinetd
```

Then we install the check-mk-agent package, ensure `/etc/xinetd.d/check_mk` exists and restart xinetd. The observium agent uses this agent to provide info to polling servers.

```
wget http://mathias-kettner.de/download/check-mk-agent_1.2.2p3-2_all.deb
dpkg -i check-mk-agent_1.2.2p3-2_all.deb
ls -l /etc/xinetd.d/check_mk
service xinetd restart
```

That will run on port **6556** so make sure you can access your monitored-device from the observium-server on that port by doing the following command:

```
observium-server:~$ telnet monitored-device 6556
```

## Enable the agent on the device

This is turned off by default so you must enable it on a per device basis.

![Enable the alerting module in the device settings](http://i.imgur.com/sIh0OA6.png)

## Install the debian package

Download the latest package section and install it using `dpkg`:

```
This deb is out of date from the actual git file

monitored-device:~$ wget https://www.dropbox.com/s/xg89ycqm5gurkzu/observium-agent_0.2.0-beta_all.deb
monitored-device:~$ dpkg -i observium-agent.deb
Unpacking observium-agent (from observium-agent.deb) ...
Setting up observium-agent (0.2.0-beta) ...
Linking the agent modules...
Link munin plugins for Observium<->Munin integration? [Y/n]:
Linking munin plugins folder /etc/munin/plugins...
Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
```

### Download locations

Damn, github disabled the downloads section...

* http://www.filedropper.com/observium-agent020-betaall
* http://depositfiles.com/files/u0bvorgwi
* http://bayfiles.com/file/HFIl/ljLV74/observium-agent_0.2.0-beta_all.deb
* https://www.dropbox.com/s/xg89ycqm5gurkzu/observium-agent_0.2.0-beta_all.deb

## Install manually

You could just copy the contents to your root (minus the `DEBIAN` folder).  You could then run the postinst file like `./postinst` or `bash postinst` which will run the install procedures.

The file locations should be the same between distros.

## References
* http://youresuchageek.blogspot.co.nz/2013/01/howto-raspberry-pi-monitor-your.html
* http://mathias-kettner.de/check_mk_download.html
* http://www.observium.org/wiki/UNIX_Agent
* CodeKiller and adama in irc://irc.oftc.net/observium
