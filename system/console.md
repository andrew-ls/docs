# Linux Virtual Console

## Fonts

Fonts in the Linux virtual console can be switched using the `setfont` command.
Linux console fonts are found in the `/lib/kbd/consolefonts` directory; fonts
have the `.psf.gz` extension. To list all available console fonts, execute:

````````````````````````````````````````````````````````````````````````````` sh
find /lib/kbd/consolefonts \
	-type f \
	-name '*.psf.gz' \
	-exec basename '{}' .psf.gz ';' \
| sort
````````````````````````````````````````````````````````````````````````````````

On Fedora, the default console font is configured with the `FONT` key in
`/etc/vconsole.conf`:

```````````````````````````````````````````````````````````````````````````` ini
FONT="default8x16"
KEYMAP="us"
````````````````````````````````````````````````````````````````````````````````

Test this configuration by executing `/usr/lib/systemd/systemd-vconsole-setup`;
if "`Unable to open tty*, fonts will not copied: Permission denied`" errors
appear, you must execute this with root privileges to propagate the font
settings to all of the mentioned TTYs.

### Terminus

One of the most versatile console fonts available is Terminus Font. On Fedora,
this font is available as the `terminus-fonts-console` package.

Once installed, `/lib/kbd/consolefonts/README.terminus` explains what typeface
each font file corresponds to:

> `````````````````````````````````````````````````````````````````````````` man
> names   mappings                covered codepage(s)
>
> ter-1*  iso01, iso15, cp1252    ISO8859-1, ISO8859-15, Windows-1252
> ter-2*  iso02, cp1250           ISO8859-2, Windows-1250
> ter-7*  iso07, cp1253           ISO8859-7, Windows-1253
> ter-9*  iso09, cp1254           ISO8859-9, Windows-1254
> ter-c*  cp1251, iso05           Windows-1251, ISO8859-5
> ter-d*  iso13, cp1257           ISO8859-13, Windows-1257
> ter-g*  iso16                   ISO8859-16
> ter-i*  cp437                   IBM-437
> ter-k*  koi8r                   KOI8-R
> ter-m*  mik                     Bulgarian-MIK
> ter-p*  pt154                   Paratype-PT154
> ter-u*  koi8u                   KOI8-U
>
> ter-v*  all mappings / code pages listed above and many others, about 110
>         language sets, 8 or 16 foreground colors depending on the kernel and
>         console driver versions
>
> names   weight
>
> ter-*n  normal
> ter-*b  bold
> ter-*v  CRT VGA bold
> ``````````````````````````````````````````````````````````````````````````````
>
> * The `ter-1*` fonts have the best coverage for Western European languages.
> * The number following the mapping token, e.g. `32` in `ter-132`, refers to the
> size (in pixels) of the font.
