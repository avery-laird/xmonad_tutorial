Handling External Media
***********************

This is also quite easy as well, thanks to a handy little python package called ``udiskie``. Here are the steps:

1. Install ``pip`` to install ``udiskie``::
	
	sudo apt-get install python-pip

2. Install ``udiskie`` using ``pip``::

	sudo pip install udiskie

3. Start ``udiskie`` on login, by placing a line in ``~/.xsessionrc``::
	
	# Start udiskie to handle media
	udiskie &

Now, any inserted media should be handled automatically by udiskie. There are many other ways of doing this (such as using nautilus or some other file browser) that are easily researched through google as well.
