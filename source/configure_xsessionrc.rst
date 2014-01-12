The ``.xsessionrc`` File
************************

Here we are, the (kind of) final step! After this, you should have a basic, working instance of xmonad. The ``.xsessionrc`` file basically sets up all the instances needed (xmobar, stalonetray, etc) at login. It's simply a bash script, with the whole "shebang" so to speak! (I couldn't resist, look `here <http://en.wikipedia.org/wiki/Shebang_(Unix)>`_ if you're a little confused)

Anyways, bad jokes aside, here's the joe-basic script that'll get you going for now. It will *have* to be place in ``~/.xsessionrc`` (you can do ``touch ~/.xsessionrc`` or like I also mentioned, ``vim ~/.xsessionrc``::

    #!/bin/bash

    # Load resources

    xrdb -merge .Xresources

    # Set up an icon tray
    stalonetray &

    # Fire up apps

    xscreensaver -no-splash &

    if [ -x /usr/bin/nm-applet ] ; then
       nm-applet --sm-disable &
    fi

    exec xmonad

Now, this is very simple: it starts stalonetray, the xscreensaver daemon, the wifi applet, and then does some magic with ``stdout`` and xmonad (look `here <http://ss64.com/bash/exec.html>`_ if you're interested). 

Congratulations! You've taken the first big step in the world of DIY window managing.

==============
Further Tweaks
==============

Now, at this point, many simple things about xmonad are working, like:

* xmonad itself
* xmobar
* stalonetray (your icon bar)
* xscreensaver

However, as I said before, xmonad doesn't assume anything -- meaning, there are many things you may still want working that xmonad does not do automatically like gnome or xfce. I chose to end part of the tutorial here for people who don't care about those things yet, but if you want the following, try out the next section:

* Wallpaper
* Automatic handling of external media (mounting cd's, usb drives, etc)
* Power management (battery info, suspension, etc)








