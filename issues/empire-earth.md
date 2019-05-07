# Empire Earth

## Linux (Wine)

### Fails to launch

This occurs when the DirectMusic library is missing. You can install it using
Winetricks.

* Install DirectMusic:

  ``````````````````````````````````````````````````````````````````````````` sh
  WINEPREFIX={WINEPREFIX} winetricks directmusic
  ``````````````````````````````````````````````````````````````````````````````

  Where `{WINEPREFIX}` is the Wine prefix the game is installed to.
