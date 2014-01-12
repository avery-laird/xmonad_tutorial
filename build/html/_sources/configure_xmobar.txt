Configuring Xmobar
******************

Here's what's inside my ``.xmobarrc``::

        Config { font = "-*-Fixed-Bold-R-Normal-*-13-*-*-*-*-*-*-*"
                , borderColor = "black"
                , border = TopB
                , bgColor = "black"
                , fgColor = "grey"
                , position = TopW L 100
                , commands = [ Run Weather "CYVR" ["-t","<tempC>C","-L","18","-H","25","--normal","green","--high","red","--low","lightblue"] 36000
                                , Run Network "eth0" ["-L","0","-H","32","--normal","green","--high","red"] 10
                                , Run Network "eth1" ["-L","0","-H","32","--normal","green","--high","red"] 10
                                , Run Cpu ["-L","3","-H","50","--normal","green","--high","red"] 10
                                , Run Memory ["-t","Mem: <usedratio>%"] 10
                                , Run Swap [] 10
                                , Run Com "uname" ["-s","-r"] "" 36000
                                , Run Date "%a %b %_d %Y %H:%M:%S" "date" 10
                                , Run StdinReader
                                ]
                , sepChar = "%"
                , alignSep = "}{"
                , template = "%StdinReader% | %cpu% | %memory% * %swap% }{<fc=#ee9a00>%date%</fc>| %eth0% - %eth1% | %uname% | %CYVR% "
                }

Whoa, that's a lot of options! Let's break it down line by line:

``, borderColor = "black"``: Defines xmobar's border colour as black.

``, border = TopB``: Draws a border at the top of xmobar's window. Black in this case, as defined in the previous setting.

``, bgColor = "black"``: Defines xmobar's background colour as black.

``, fgColor = "grey"``: Defines the default font colour as grey.

``, position = TopW L 94``: Defines the position of xmobar as the top of the screen, on the left hand side, taking up 100% of width of the screen.

``, commands = []``: This defines a list of commands, or things to do when xmobar starts up. All of the newlines starting with a comma and ``Run`` define different ways of getting information from different areas of the system, and how to display that information on the bar.

``, sepChar = "%"``: Character to be used for indicating commands in the output template. (``%`` is the default anyways).

``, alignSep = "}{"``: The characters that define which commands in the output template are aligned left, and which are aligned right. Any commands on the left side of a ``}`` are aligned to the left side, and any on the right side of a ``{`` are aligned to the right side. This will make a bit more sense in the next (and final) explanation.

``, template = "%StdinReader% | %cpu% | %memory% * %swap% }{<fc=#ee9a00>%date%</fc>| %eth0% - %eth1% | %uname% | %CYVR% "``: This one may not be immediately obvious at first glance. Basically, this is a template to define how the data retrieved by the various commands we ran earlier should be displayed. Going from left to right, it says that the data from ``StdinReader``, CPU usage, memory usage and swap usage should be shown on the left. Now we see here our friends the curly braces; as I explained before, they say that all that data should be on the left hand side. On the right hand side is the date (in orange, as defined by the ``<fc>`` tags), the download and upload speeds, kernel name and the temperature. I live in Vancouver, hence ``CYVR``. *You'll have to change that value to your area code.*

==============
Final thoughts
==============

You may not understand completely how the configuration file works at first, however give it time and slowly it will start to make sense. As we continue to delve deeper into the xmonad universe, the various connections between files will become more and more easy to follow. I promise! On we go to configuring stalonetray.
