# MIDI

## Hardware

### Sound Blaster Live/Audigy

#### Soundfont

MIDI hardware must be loaded with a soundfont in order to play MIDI music.
On-board memory for these soundfonts is limited however, so we will need to
download and install a relatively small one. One example would be the
[Default Windows MIDI Soundfont](https://musical-artifacts.com/artifacts/713).

Assuming the soundfont we are setting up is named `gm.sf2`, we will now
integrate it with our system:

````````````````````````````````````````````````````````````````````````````` sh
sudo mkdir -p '/usr/local/share/soundfonts'
sudo mv 'gm.sf2' '/usr/local/share/soundfonts/gm.sf2'
sudo chown root:root '/usr/local/share/soundfonts/gm.sf2'
sudo chmod 644 '/usr/local/share/soundfonts/gm.sf2'
````````````````````````````````````````````````````````````````````````````````

#### Loader

With a soundfont available, we need a program to load it into the MIDI hardware.
Install the `awesfx` package, which includes the `asfxload` program. Once
installed, we can create a systemd unit to load the soundfont on system startup.

Execute `sudo -e /etc/systemd/system/asfxload.service` to open an editor for our
new systemd unit, and enter the following:

```````````````````````````````````````````````````````````````````````` systemd
[Unit]
Description=SoundFont loader

[Service]
Type=oneshot
ExecStart=/usr/bin/asfxload '/usr/local/share/soundfonts/gm.sf2'

[Install]
WantedBy=multi-user.target
````````````````````````````````````````````````````````````````````````````````

Once saved, execute `sudo systemctl enable asfxload.service` to enable the unit.

### References

* [Ubuntu Community Help Wiki](https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup)

## Software

If your device lacks hardware MIDI support, you will need to install a software
synthesizer such as [FluidSynth](http://fluidsynth.org).
