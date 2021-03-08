About Ardour flatpak
====================

Some notes about this Flatpak.

Dependencies
------------

The dependencies for Ardour are non standard. We try to use what is
listed at https://nightly.ardour.org/list.php#build_deps

This is to provide the best experience to upstream binary builds.

Plugins support
---------------

The package supports LV2, LADSPA, DSSI and Linux VST/VST3 plugins
built for Flatpak. You cannot install or use plugins not packaged as a
Flatpak. There is no support for Win32 emulated VST either.

Before upgrading the runtime used, please consider that the plugins
need to be upgraded first. Provision is made for plugins to live in
branches as to be available for different runtimes.

Jack audio support
------------------

You need to install the package `pipewire-jack-audio-connection-kit` or
equivalent in your distro. This might mean that you have to uninstall
JACK if you had it installed.

Then, just open Ardour and it will work with the Pipewire implementation of
JACK, out of the box.

ALSA Device reservation
-----------------------

Ardour requires exclusive use of the ALSA sound device. To that effect
it supports the device reservation D-Bus interface, hence the
`--own-name=org.freedesktop.ReserveDevice1.*` permission.
