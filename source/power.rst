Power Management in xmonad
**************************

Okay, this is also simple as well:

1. Install ``xfce4-power-manager``::

	sudo apt-get install xfce4-power-manager

2. Start it on login, in the ``~/.xsessionrc`` file. Once again, this should be after the shebang but before the ``if`` statements::

	xfce4-power-manager &

The power manager icon should now show up in stalonetray.

	
