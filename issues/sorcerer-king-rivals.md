# Sorcerer King: Rivals

## Linux (Wine)

### (Proton) Crashes after splash screen

* Change the Steam launch arguments to:

  ``````````````````````````````````````````````````````````````````````````` sh
  PROTON_USE_WINED3D=1 %command%
  ``````````````````````````````````````````````````````````````````````````````

### Text does not render

This is caused by an incompatibility with the game's font.

* Remove/rename `SDNXLFonts.dll` in the installation directory.
