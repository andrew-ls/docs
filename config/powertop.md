# PowerTOP

## Initial Configuration

Run `powertop --auto-tune` with root privileges. Once the application interface
appears, switch to the "Tunables" tab. Here you can see a list of all tunable
options for your system, with their current status displayed to the left: a
status of "Good" means the tunable option is in the best state for saving power;
a status of "Bad" means the opposite.

The `--auto-tune` option should have set all tunable options to their "Good"
state. You may notice problems manifesting when some tunables are in their
"Good" state, for example your Bluetooth adapter might stop working left idle
for too long; if that is the case, find the appropriate tunable option and
toggle it to its "Bad" status, noting the command displayed at the top left of
the application: this is the shell command executed to effect the tunable
option's status.

If you decide to configure your system to run PowerTOP on boot, you should also
make sure the commands used to effect any "Bad" statuses you require are run
after the main `powertop --auto-tune` process executes. These commands must be
executed by a shell process, so pass the command as an argument to be executed
by a shell program such as `/bin/sh`.

## Using systemd

After installing PowerTOP a systemd unit file should be available at
`/usr/lib/systemd/system/powertop.service`. This should suffice if you do not
need to set any tunable option states to "Bad", otherwise you should copy this
unit file to `/etc/systemd/system` and edit it.

The systemd unit below shows how to effect a "Bad" state using an
`ExecStartPost` directive; you can repeat these as many times as necessary to
effect all the "Bad" states you need:

```````````````````````````````````````````````````````````````````````` systemd
[Unit]
Description=PowerTOP autotuner

[Service]
Type=oneshot
ExecStart=/usr/sbin/powertop --auto-tune
ExecStartPost=/bin/sh -c "echo 'on' > '/sys/bus/usb/devices/usb1/power/control'"

[Install]
WantedBy=multi-user.target
````````````````````````````````````````````````````````````````````````````````

Execute `systemctl enable powertop` with root privileges to enable the service
to automatically run on boot.
