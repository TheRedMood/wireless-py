Wireless-py
===========

Info
----
wireless-py is meant to make the use of wireless networks easier on _OpenBSD_.
It utilizes `python2.7` by default, but is fully compatible with any version
above `2.3`.

It was inspired by [overrider/wireless](https://github.com/overrider/wireless).

Usage
-----
Networks are added using the `/etc/wireless-py.conf` file. This file follows
this syntax:

```Conf
# This is a comment,
;   ... And so is this

# The config header and it's interface value are REQUIRED.
[config]
interface=wlan0

# The section header is the network name
# Values supported is:
#   nwid - SSID of network. Defaults to the section name.
#   wpakey - network password. Defaults to ''
#   type - open or wpa. Defaults to open.
[work]
nwid=SSID_work
type=wpa
wpakey=secret_password.

[home]
nwid=dlink444
type=open

# Same as [home], since type defaults to open
[home implicit]
nwid=dlink444
```

The `wireless-py` tool is used like this:

```Shell
# Listing networks
% wireless-py

# Connecting to a network.
% wireless-py NETWORK_NAME
```

Setup
-----

Execute these commands as root:

```Shell
% cp wireless-py /usr/local/bin/wireless-py
% cp wireless-py.conf /etc/wireless-py.conf
```

Since you are going to be storing passwords in the `/etc/wireless-py.conf`,
one might want to make sure that the file can only be read by the root user. To
do so, execute the following command as the root user:

```Shell
% chown root:wheel /etc/wireless-py.conf
% chmod 0600 /etc/wireless-py.conf
```

You then want to edit `/etc/wireless-py.conf` to reflect your network setup.

