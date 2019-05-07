# Survival Crisis Z

## Windows

### Crashes on launch with error `Run-time error '429': ActiveX component can't create object`

This occurs when DirectX 7/8 Visual Basic and Direct3D Retained Mode DLLs are
not available.

* Install and register the necessary DLLs:
  * Acquire `dx7vb.dll`, `dx8vb.dll`, and `d3drm.dll`.
  * Place the DLLs into `%SystemRoot%\System32`.
  * Open an administrator command prompt and change directory to
    `%SystemRoot%\System32`.
  * Execute `regsvr32 dx7vb.dll` and `regsvr32 dx8vb.dll`.

## Linux (Wine)

### Fails to launch with error `err:module:import_dll Library MSVBVM60.DLL (which is needed by L"…") not found`

This occurs when the Microsoft Visual Basic 6.0 virtual machine DLL is not
available.

* Install the DLL for the game:
  * Acquire `MSVBVM60.DLL` and place it into the Survival Crisis Z installation
    directory.
