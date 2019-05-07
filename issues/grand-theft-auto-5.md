# Grand Theft Auto V

## Linux (Wine)

### GTA Online crashes on load

* Change the game launch arguments on Steam:

  ``````````````````````````````````````````````````````````````````````````` sh
  WINEDLLOVERRIDES='winedbg.exe=d' %command%
  ``````````````````````````````````````````````````````````````````````````````
