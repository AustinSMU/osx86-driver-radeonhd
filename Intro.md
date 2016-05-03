# Introduction #

ATI Radeon HD series driver (all ATOMBIOS based cards including mobility).
Initial port from linux RadeonHD code (version 1.2.5)

# HOWTO install #

Put it into /S/L/E/ and rebuild the cache to test. It will not affect vanilla driver.
Any injector will prevent this driver from loading since it works the same way as IONDRVSupport.

# Use Details #

Add your content here.  Format your content with:

  * version without **AtomBios** may only works for cards with quirk table included in Linux code.
  * list of cards with quirk table Attached File  _knownCardList.txt_ ( 3.72K )
  * Info.plist has some custom options:
    * Set "debugMode" to true will disable switch resolution and boot with VESA mode, which may help gathering debug information if normal mode not works for you.
    * Put your EDID data in "EDID", it will be used if autodetect EDID failed.
    * Set "verboseLevel" to 0 if you don't want the debug information.
    * Set "enableHWCursor" to false if you don't want HW cursor.
  * The driver may sometimes causes KP during boot, please confirm if it's no longer an issue.
  * Some users are looking for QE/CI here. You should first get to know that framebuffer driver is not dedicated for QE/CI. If your card is not supported by ATIRadeonX1000/2000 kexts, there is no chance this framebuffer driver will help you.
  * If you get a blank or dark screen after boot, try set "enableBacklight" to false in Info.plist. Low backlight value planned support in next release.

[10/28/2009 update]:
  * Initial support for HardwareCursor:
  * Good: No more mouse tearing for me;
  * Bad: mouse cursor is skewed.

  * switch to rewrite all code, making them inherited from IOFramebuffer planned (based on OMNI suggestion).

[10/20/2009 update]:
  * Finally get the VoodooDumpMsg work, it will help with debug. Run "RadeonDump" in terminal after entering desktop will produce full debug messages without leftout. No other function added. Thanks ole2 for the reminding.

[10/17/2009 update]:
  * Since some card need the Backlight tuning step, some don't, I add an option "enableBacklight" in Info.plist and default to on. Set it to off if default is not work.

[10/14/2009 update]:
  * Add some common resolutions if only the native one is detected. Provide a card name to be displayed in system profile. Both are 32 bit AtomBios version.

[10/13/2009 update]:
  * A x1300 mobility user successfully entered desktop with native resolution but backlight turned off after that. Here is the version removed the backlight tuning steps in case you run into the same condition.

[10/12/2009 update]:
  * All works for my x1400, but you need test to see if it works for you or not.

# Build Details #

The only difference in source codes for 10.5 and 10.6 is located in xf86.h. Well, of course the IOKit header files are different too.

