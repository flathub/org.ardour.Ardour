About Ardour flatpak
====================

Some notes about this Flatpak, for developers / maintainer.

Dependencies
------------

The dependencies for Ardour are non standard. We try to use what is
listed at https://nightly.ardour.org/list.php#build_deps

This is to provide the closest from upstream binary builds.

Plugins support
---------------

The package supports LV2, LADSPA, and Linux VST/VST3 plugins
built for Flatpak.

Before upgrading the runtime used, please consider that the plugins
need to be upgraded first. Provision is made for plugins to live in
branches as to be available for different runtimes.

## User installed plugins

Plugins in `~/.vst3`, `~/.vst` and `~/.lv2` may work if they are built
properly. There is no universal solution if they depend on .so that are
not available or incompatible.

There is no support for Win32 emulated VST.

Network access
--------------

Starting Ardour 7, network access is granted for the loop library.

The Media library of MIDI files is installed at build time.

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
