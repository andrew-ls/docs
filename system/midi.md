# MIDI

## Soundfonts

### Installation

MIDI hardware and software must be loaded with a soundfont in order to play MIDI
music. First you must have a soundfont file such as:

* [Default Windows MIDI](https://musical-artifacts.com/artifacts/713)
  (3.2 MB)
* [¥Weeds¥ General MIDI](http://www.simpilot.net/~richnagel/#downloads)
  (54.9 MB)

Once you have acquired a soundfont file, you can integrate it with your system.
Assuming the soundfont we are setting up is named `gm.sf2`, execute the
following to install the soundfont to the `/usr/local/share/soundfonts`
directory:

````````````````````````````````````````````````````````````````````````````` sh
sudo mkdir -p '/usr/local/share/soundfonts'
sudo mv 'gm.sf2' '/usr/local/share/soundfonts/gm.sf2'
sudo chown root:root '/usr/local/share/soundfonts/gm.sf2'
sudo chmod 644 '/usr/local/share/soundfonts/gm.sf2'
````````````````````````````````````````````````````````````````````````````````

## Hardware

### Sound Blaster Live/Audigy

With a soundfont available, we need a program to load it into the MIDI hardware.
Install the `awesfx` package, which includes the `asfxload` program. Once
installed, test your soundfont by executing `asfxload [SOUNDFONT]`, where
`[SOUNDFONT]` is the path to a soundfont. On-board memory for soundfonts is
limited, so if `asfxload` fails with the error "`sfxload: no memory left`" you
must choose a smaller soundfont.

Once you have ensured that your chosen soundfont loads correctly, you can create
a systemd unit to load the soundfont on system startup.

Execute `sudo -e /etc/systemd/system/asfxload.service` to open an editor for our
new systemd unit, and enter the following (where `[SOUNDFONT]` is the path to
your chosen soundfont):

```````````````````````````````````````````````````````````````````````` systemd
[Unit]
Description=SoundFont loader

[Service]
Type=oneshot
ExecStart=/usr/bin/asfxload '[SOUNDFONT]'

[Install]
WantedBy=multi-user.target
````````````````````````````````````````````````````````````````````````````````

Once saved, execute `sudo systemctl enable asfxload.service` to enable the unit.

### References

* [Ubuntu Community Help Wiki](https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup)

## Software

If your device lacks hardware MIDI support, you will need to install a software
synthesizer such as [FluidSynth](http://fluidsynth.org).
