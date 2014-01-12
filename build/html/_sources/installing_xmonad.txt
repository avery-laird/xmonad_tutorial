.. _installing-xmonad:

Installing Xmonad
*****************

When installing xmonad, pretty much any package manager will do. You can even compile from source, but if you're reading the beginning beginner's guide to xmonad, I would recommend against that unless you follow an extremely clear guide (like this). I use APT for package management.

===================================
Install xmonad and some handy tools
===================================

Install xmonad and dmenu:

``sudo apt-get install xmonad suckless-tools xscreensaver`` 

The package ``suckless-tools`` installs dmenu on my latest version of ubuntu just fine. Older versions may have to install ``dwm-tools`` instead, and other distros might have to search for dmenu as a separate package. Dmenu is a bit of a must-have for getting started, because it allows the execution of applications easily, as we'll see later. If you decide for some reason later on that dmenu is not for you, it's easily uninstallible however I recommend that you get started with dmenu. The ``xscreensaver`` package will be used later on, with handling lock screens.

===========================================================
Configuration and tweaking (and maybe some more installing)
===========================================================

If you were to login using xmonad right now, you would be greeted with an entirely black screen. For the sake of simplicity, let's hold off on that just yet and do a bit more housework first. Next we're going to install xmobar, a handy status bar popular among xmonad users. Like before, I'm going to use APT to install:

``sudo apt-get install xmobar``

Once again, xmonad would still show us a nice black screen. Like pretty much anything in xmonad, xmobar requires some hefty configuration to start looking pretty. That configuration is supplied by a file in your home directory, ``~/.xmobarrc``. You might have to create it, or it may already be there. If it's not there, do ``touch ~/.xmobarrc``, and use any text editor you like to make the nessecary changes. I prefer vim for small things like this. With that done, let's move on to the next section.  
