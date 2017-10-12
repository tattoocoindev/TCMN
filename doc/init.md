Sample init scripts and service configuration for Tattood
==========================================================

Sample scripts and configuration files for systemd, Upstart and OpenRC
can be found in the contrib/init folder.

    contrib/init/Tattood.service:    systemd service unit configuration
    contrib/init/Tattood.openrc:     OpenRC compatible SysV style init script
    contrib/init/Tattood.openrcconf: OpenRC conf.d file
    contrib/init/Tattood.conf:       Upstart service configuration file
    contrib/init/Tattood.init:       CentOS compatible SysV style init script

1. Service User
---------------------------------

All three startup configurations assume the existence of a "Tattoo" user
and group.  They must be created before attempting to use these scripts.

2. Configuration
---------------------------------

At a bare minimum, Tattood requires that the rpcpassword setting be set
when running as a daemon.  If the configuration file does not exist or this
setting is not set, Tattood will shutdown promptly after startup.

This password does not have to be remembered or typed as it is mostly used
as a fixed token that Tattood and client programs read from the configuration
file, however it is recommended that a strong and secure password be used
as this password is security critical to securing the wallet should the
wallet be enabled.

If Tattood is run with "-daemon" flag, and no rpcpassword is set, it will
print a randomly generated suitable password to stderr.  You can also
generate one from the shell yourself like this:

bash -c 'tr -dc a-zA-Z0-9 < /dev/urandom | head -c32 && echo'

Once you have a password in hand, set rpcpassword= in /etc/Tattoo/Tattoo.conf

For an example configuration file that describes the configuration settings,
see contrib/debian/examples/Tattoo.conf.

3. Paths
---------------------------------

All three configurations assume several paths that might need to be adjusted.

Binary:              /usr/bin/Tattood
Configuration file:  /etc/Tattoo/Tattoo.conf
Data directory:      /var/lib/Tattood
PID file:            /var/run/Tattood/Tattood.pid (OpenRC and Upstart)
                     /var/lib/Tattood/Tattood.pid (systemd)

The configuration file, PID directory (if applicable) and data directory
should all be owned by the Tattoo user and group.  It is advised for security
reasons to make the configuration file and data directory only readable by the
Tattoo user and group.  Access to Tattoo-cli and other Tattood rpc clients
can then be controlled by group membership.

4. Installing Service Configuration
-----------------------------------

4a) systemd

Installing this .service file consists on just copying it to
/usr/lib/systemd/system directory, followed by the command
"systemctl daemon-reload" in order to update running systemd configuration.

To test, run "systemctl start Tattood" and to enable for system startup run
"systemctl enable Tattood"

4b) OpenRC

Rename Tattood.openrc to Tattood and drop it in /etc/init.d.  Double
check ownership and permissions and make it executable.  Test it with
"/etc/init.d/Tattood start" and configure it to run on startup with
"rc-update add Tattood"

4c) Upstart (for Debian/Ubuntu based distributions)

Drop Tattood.conf in /etc/init.  Test by running "service Tattood start"
it will automatically start on reboot.

NOTE: This script is incompatible with CentOS 5 and Amazon Linux 2014 as they
use old versions of Upstart and do not supply the start-stop-daemon uitility.

4d) CentOS

Copy Tattood.init to /etc/init.d/Tattood. Test by running "service Tattood start".

Using this script, you can adjust the path and flags to the Tattood program by
setting the TattooD and FLAGS environment variables in the file
/etc/sysconfig/Tattood. You can also use the DAEMONOPTS environment variable here.

5. Auto-respawn
-----------------------------------

Auto respawning is currently only configured for Upstart and systemd.
Reasonable defaults have been chosen but YMMV.
