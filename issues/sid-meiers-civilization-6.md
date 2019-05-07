# Sid Meier's Civilization VI

## Linux

### Fails to launch with error `./GameGuide/Civ6: symbol lookup error: /lib64/libfontconfig.so.1: undefined symbol: FT_Done_MM_Var`

You need to select the correct FreeType library for the Aspyr launcher to use.

* Get the path of the FreeType library:

  ``````````````````````````````````````````````````````````````````````````` sh
  whereis -b libfreetype
  ``````````````````````````````````````````````````````````````````````````````

* Change the game launch arguments on Steam to load the library (assuming the
  path is `/usr/lib64/libfreetype.so`):

  ``````````````````````````````````````````````````````````````````````````` sh
  LD_PRELOAD='/usr/lib64/libfreetype.so' %command%
  ``````````````````````````````````````````````````````````````````````````````

### Graphical corruption on AMD Radeon RX Vega

* Change the launch arguments on Steam to:

  ``````````````````````````````````````````````````````````````````````````` sh
  R600_DEBUG='nir' %command%
  ``````````````````````````````````````````````````````````````````````````````
