OSX branch notes
================

This is an experimental port of the FPDB HUD to Cocoa.  It presently
supports only the PokerStars client.

Why?
----

The GTK HUD is great, but the GTK code for keeping the HUD windows on
top of tables doesn't work with native poker client windows, because
it can only see windows in your X server.  This project might be the
answer: http://gtk-osx.sourceforge.net/ but I wanted an excuse to mess
around with Cocoa.

How?
----

Grab the code from this git branch and proceed as in
[the fpdb git guide](http://sourceforge.net/apps/mediawiki/fpdb/index.php?title=Install_With_Git).
You will also need to build the _axlib_ framework included in the
pyfdb/axlib/ directory.  This framework is used to access some
windowing notifications that aren't available directly in python or
through pyobjc.  Open axlib.xcodeproj in XCode and build in Release
mode.  Finally, you will need to enable access for assistive devices
in the Universal Access pane of System Preferences.  This allows axlib
to register for window notifications using the accessibility API.

Caveats/Known Bugs
------------------

* Auxiliary windows are not supported as yet.  If you have them in
  your HUD_config.xml, Bad Things may happen.  Back it up and remove
  them.  And send me an email telling me I'm lazy, I might get around
  to fixing it.
* Right-click popup of all stats on HUD stat windows
  is not implemented yet.
* If you have multiple tables open with names like "Ichabod", "Ichabod
  II" etc, the HUD may get confused.
* PokerStars must be open when you start the HUD.
* Middle-click hiding of stat windows is not implemented.