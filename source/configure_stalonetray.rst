Configuring Stalonetray
***********************

Stalonetray is a small "stand-alone" tray, nice easy and simple to use. It's installed with a simple APT command: ``sudo apt-get install stalonetray``. Like xmobar, it also gets it's parameters from a file in your home directory called ``~/.stalonetrayrc``. Also like xmobar, if the file does not yet exist, create it.

Here's what my stalonetray configuration looks like::

	decorations none
	transparent false
	dockapp_mode none
	geometry 5x1-400+0
	max_geometry 5x1-325-10
	background "#000000"
	kludges force_icons_size
	grow_gravity NE
	icon_gravity NE
	icon_size 12
	sticky true
	#window_strut none
	window_type dock
	window_layer bottom
	#no_shrink false
	skip_taskbar true
 
I will go into less detail for these options than xmobar, because the documentation is more or less quite easy to understand. I will touch on the more important ones, however:

``geometry 5x1-523+0``: The first two values, ``5x1`` are the height and width of the bar (measured in multiples of icon slots, e.g. 5 icons wide and 1 icon high). The next two are the ``x`` and ``y`` positions.

``background "#000000"``: Black background, to match xmobar.

=========
What Next
=========

If you were to run stalonetray right now, most likely it would simply be an empty black bar. With no icons to fill it, it would just blend right in with xmobar. In the next part, however, when we configure the ``xmonad.hs`` file, processes will be started on login and will populate stalonetray. Let's get started! 


