ATTENSION!!
===========

This was originally forked from pythonanywhere/shellinabox_fork, not gilesp!
The pythonanwhere fork is officially dead and this fork now takes it's place.
The gilesp fork has been in a coma for years, and should be considered dead.
There is about to be a resync with our sister repo shellinabox/shellinabox,
and I hope to be able to find a way to re-base the repo at that time so we can
do pull requests and get things going.


MAJOR CHANGES
=============

This fork has a redesigned color system, better tmux compatibility and support
for some basic swipe gestures in tmux.  It fixes the old iframe bug, and many
others.


Updating software
=================

Always best to update the software and firmware.

	apt-get update


Installing necessary applications
=================================

Install some applications before proceeeding.

	apt-get install git dpkg-dev debhelper autotools-dev libpam0g-dev libpam0g lighttpd


Installing and configuring Shell In A Box
=========================================

Clone the current git repository of Shell In A Box.

	git clone https://github.com/rsolomou/shellinabox_fork.git
	cd shellinabox_fork

Build the package

	dpkg-buildpackage
	dpkg -i ../shellinabox_2.14-1_armhf.deb

Edit the settings file.

	nano /etc/default/shellinabox

Change the arguments passed to the ones below:

	SHELLINABOX_ARGS="--no-beep -s /terminal:LOGIN --disable-ssl --localhost-only"

Restart the Shell In A Box service.

	/etc/init.d/shellinabox restart


Configuring lighttpd
====================

Set the proxy settings for redirecting to /terminal.

	cd /etc/lighttpd/conf-enabled
	ln -s ../conf-available/10-proxy.conf
	nano /etc/lighttpd/lighttpd.conf

Add the following to the end of the file:

     proxy.server = (
          "/terminal" =>
               ( (
                    "host" => "127.0.0.1",
					"port" => 4200
               ) )
     )

Restart the lighttpd service.

	/etc/init.d/lighttpd restart


Finishing
=========

You should now be able to see your Shell In A Box terminal when you visit the following link:

	http://raspberry-pi-ip/terminal


Links & Credits
===================

* [Original Tutorial](http://blog.remibergsma.com/2013/03/15/always-available-linux-terminal-shell-in-a-box-on-raspberry-pi/)
* [Original Repository](https://github.com/pythonanywhere/shellinabox_fork)
