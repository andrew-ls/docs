# One Finger Death Punch

## Linux (Wine)

### Fails to launch

This occurs when .NET Framework 4.0 is missing. You can install it using
Winetricks.

* Install .NET Framework 4.0:

  ``````````````````````````````````````````````````````````````````````````` sh
  WINEPREFIX={WINEPREFIX} winetricks dotnet40
  WINEPREFIX={WINEPREFIX} winetricks dotnet40
  ``````````````````````````````````````````````````````````````````````````````

  Where `{WINEPREFIX}` is the Wine prefix the game is installed to; for the
  Steam version, this will be `compatdata/264200/pfx` within the `steamapps`
  library the game is installed to.

  The duplication above is not a typo: .NET Framework 4.0 must be installed and
  then repaired (by repeating the installation command).
