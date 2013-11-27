Updating software
=================

Always best to update the software and firmware.

	apt-get update
	apt-get upgrade


Installing necessary applications
=================================

Install some applications before proceeeding.

	apt-get install git dpkg-dev debhelper autotools-dev libssl-dev libpam0g-dev zlib1g-dev libssl1.0.0 libpam0g openssl lighttpd


Installing and configuring Shell In A Box
=========================================

Clone the current git repository of Shell In A Box.

	git clone https://github.com/rsolomou/shellinabox_fork
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
