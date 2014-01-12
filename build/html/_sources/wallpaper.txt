Wallpaper
*********

This is really simple and easy to do, and there are a huge number of ways to do it. This is my method, using ``feh``.

1. First, install ``feh``::

	sudo apt-get install feh

2. Second, configure the wallpaper to be set on startup. For this, we'll need the ``~/.xsessionrc`` file. Place this line somewhere in ``.xsessionrc``, after ``#!/bin/bash`` but before the ``if`` statements::

	# Set background image with feh
	feh --bg-scale /usr/share/backgrounds/warty-final-ubuntu.png &

This just invokes ``feh`` and tells it which image to set as the background. I have the default warty background here, but you can change the file path to any image you want.
