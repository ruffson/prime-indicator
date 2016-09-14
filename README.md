PRIME Indicator
===============
Indicator applet for Ubuntu 14.04 and higher laptop users with NVIDIA/Intel hybrid GPUs,
allowing quick switch between the GPUs in matter of seconds.
It has been tested on Ubuntu 16.04 only, but should be working just as well
on any Ubuntu distribution more recent than 12.04, including Xubuntu, Kubuntu and Lubuntu flavours.
Ubuntu 12.04 users should also have no problems, as long if installing with the newest hardware enablement stack.

This version features full power saving by completely disabling the NVIDIA GPU when it's not being used. 
NVIDIA PRIME won't do it by default, leaving NVIDIA GPU powered on even when it's using the Intel GPU only.
While this saves some power (because the NVIDIA GPU is idle), it still consumes about 4~5W more than with it 
completely off. Since this is not ideal, this version is extended to use bbswitch to power the NVIDIA GPU off. 
Still, should the need for it to be on arrive, this version provides an option to force it to stay powered on
when using integrated graphics only, so it can be used for GPGPU and other tasks other than rendering.

Prerequisites
=============
Make sure you have installed and enabled:

* NVIDIA driver, version 331.20 or higher
* NVIDIA's additional package, `nvidia-prime`
* `mesa-utils` package
* `python` package
* `python-appindicator` package
* `python-configparser` package
* `bbswitch-dkms` package

Or simply run the following, which will install all dependencies and the latest NVIDIA driver for your GPU (if it's supported by NVIDIA's latest drivers).
```
sudo apt-get install python3 python3-gi mesa-utils nvidia-prime nvidia-settings bbswitch-dkms
sudo apt-get install $(sudo ubuntu-drivers devices | grep -o nvidia-[[:digit:]]*)
```

Troubleshooting
===============

### `appindicator` module missing
Install the `python-appindicator` package.

### `configparser` module missing
Install the `python-configparser` package.

### Couldn't find RGB GLX visual or fbconfig
Install the `mesa-utils` package.

### PRIME Indicator only shows a question mark icon
If you're using `UEFI`, try disabling `Secure Boot` as NVIDIA's proprietary driver does NOT work with `Secure Boot` enabled and it might result in neither GPU being recognized.


Installation
============
```shell
chmod a+x setup.sh
sudo ./setup.sh
```
