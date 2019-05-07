# Sid Meier's Civilization IV

## Linux (Wine)

### Game world does not render, other miscellaneous errors

This occurs when the Microsoft XML Core Services library is missing. You can
install it using Winetricks.

* Install MSXML:

  ``````````````````````````````````````````````````````````````````````````` sh
  WINEPREFIX={WINEPREFIX} winetricks msxml3
  ``````````````````````````````````````````````````````````````````````````````

  Where `{WINEPREFIX}` is the Wine prefix the game is installed to; for the
  Steam version, this will be `compatdata/3900/pfx` within the `steamapps`
  library the game is installed to.
