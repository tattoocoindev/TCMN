
Debian
====================
This directory contains files used to package Tattood/Tattoo-qt
for Debian-based Linux systems. If you compile Tattood/Tattoo-qt yourself, there are some useful files here.

## Tattoo: URI support ##


Tattoo-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install Tattoo-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your Tattooqt binary to `/usr/bin`
and the `../../share/pixmaps/Tattoo128.png` to `/usr/share/pixmaps`

Tattoo-qt.protocol (KDE)

