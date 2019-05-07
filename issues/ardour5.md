# Ardour 5

### Quits with 'Could not create session…'

You are currently not authorised for real-time audio access using
[JACK](http://jackaudio.org).

* In a command-line shell enter the following command with root privileges to
  add your user to the `jackuser` group for these privileges:

  ``````````````````````````````````````````````````````````````````````````` sh
  usermod -aG jackuser ${LOGNAME}
  ``````````````````````````````````````````````````````````````````````````````

* Then log out and in again.
