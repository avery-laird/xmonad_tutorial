Configuring Xmonad.hs
*********************

Now we are nearing the point where we could login to xmonad and be greeted by some friendly readouts, and perhaps a sign that the login was successful. As everything stands now:

* xmonad and dmenu are installed
* xmobar is installed and configured
* stalonetray is installed and configured

Next, we have to configure xmonad itself. As you might have noticed, we're following a bit of a pattern: install the software, configure the software and etc. After that, we tie it all together in the ``~/.xsessonrc`` file which is where all of the software is started during login. Once they're started up, the software then references their config files. 

=====================
Xmonad file structure
=====================

The configuration files for xmonad are layed out a little bit like this::

	~/.xmonad
    	     |
    	     +-- xmonad.hs

Now, a lot of the time (or at least some of the time) you have to create this file structure yourself. This is quite simple.

``sudo mkdir ~/.xmonad && cd ~/.xmonad``

And then:

``touch xmonad.hs``

Or if you're like me and like to skip steps (and have vim installed) then you can do:

``vim xmonad.hs``

Notice the period before ``.xmonad`` and lack of period before ``xmonad.hs``. This is important to get right.

================
Configure Xmonad
================

``Xmonad.hs`` is written in Haskell (as is the rest of xmonad itself) and can contain pretty any configuration you like. Mine is rather simple, and is a mish mash of various things I've found on the web and various things I've done myself::

	import XMonad
	import XMonad.Hooks.DynamicLog
	import XMonad.Hooks.ManageDocks
	import XMonad.Util.Run(spawnPipe)
	import XMonad.Util.EZConfig(additionalKeys)
	import System.IO

	main = do
	    xmproc <- spawnPipe "xmobar"

	    xmonad $ defaultConfig
	        { manageHook = manageDocks <+> manageHook defaultConfig
	        , layoutHook = avoidStruts  $  layoutHook defaultConfig
	        , logHook = dynamicLogWithPP xmobarPP
        	                { ppOutput = hPutStrLn xmproc
                	        , ppTitle = xmobarColor "green" "" . shorten 50
	                        }
	        , modMask = mod4Mask     -- Rebind Mod to the Windows key
	        } `additionalKeys`
	        [ ((mod4Mask .|. shiftMask, xK_z), spawn "xscreensaver-command -lock; xset dpms force off")
	        , ((controlMask, xK_Print), spawn "sleep 0.2; scrot -s")
	        , ((0, xK_Print), spawn "scrot")
	        ]

I won't go into large detail like I have with the other files, mostly because this isn't so much a configuration file as an entity of xmonad itself and also because the documentation on Haskell (and xmonad with Haskell) are quite extensive. If you're interested, `here <http://www.haskell.org/haskellwiki/Xmonad>`_ is a good place to start.

The most notable things about this file you need to now is that the primary xmonad key (which you may not know, but so far has been Mod/ALT) is remapped to the Meta, or Windows, key. The last two lines are for taking screen shots (which I barely use) but one useful keybinding (``Shift + Meta + Z``) is for locking the screen. It invokes ``xscreensaver-command -lock`` and then ``xset dpms force off`` to actually switch off the monitor (I've found that my laptop backlight stays on, and in an effort to save power and pixels I have included this command as well). For extensive config examples and inspiration, try looking on the web -- or try something like `this <http://www.vicfryzel.com/2010/06/27/obtaining-a-beautiful-usable-xmonad-configuration>`_.
 
