# Anbox

## Installation

Follow the instructions within the
[official Anbox documentation](https://docs.anbox.io/userguide/install.html).
Note that Anbox is only distributed as a Snap package, so `snapd` must be
installed on your system.

## Google Play Services

Many Android applications require the proprietary Google Play Services installed
to function correctly. We can use the "anbox-playstore-installer" script to
automate the installation and configuration of Google Play Services within your
Anbox Android image.

Before continuing, ensure `wget`, `lzip`, `unzip`, and `squashfs-tools` are
installed on your system.

We can begin by downloading the script and marking it as executable:

````````````````````````````````````````````````````````````````````````````` sh
wget 'https://raw.githubusercontent.com/geeks-r-us/anbox-playstore-installer/master/install-playstore.sh'
chmod +x 'install-playstore.sh'
````````````````````````````````````````````````````````````````````````````````

Next, execute the following to discover where your Android image is located:

````````````````````````````````````````````````````````````````````````````` sh
find /snap /var -name 'android.img' 2> /dev/null
````````````````````````````````````````````````````````````````````````````````

If the command prints "`/snap/anbox/current/android.img`", then no modification
of the script is necessary. If, however, a different path is printed, we must
replace "`/snap/anbox/current/android.img`" with the path that was printed.

If your version of `sed` supports in-place editing, you can use the following
commands to automatically perform this replacement:

````````````````````````````````````````````````````````````````````````````` sh
IMAGE="$(find /snap /var -name 'android.img' 2> /dev/null | head -n 1)"
sed -i -e "s|/snap/anbox/current/android.img|${IMAGE}|" install-playstore.sh
````````````````````````````````````````````````````````````````````````````````

Otherwise, you must make this replacement within the script yourself.

Once the script is ready, execute `killall anbox` to make sure Anbox is not
still running, then execute `sudo ./install-playstore.sh` to perform the
installation.

### References

* [Linux Uprising](https://www.linuxuprising.com/2018/07/anbox-how-to-install-google-play-store.html?showComment=1533506821283#c4415289781078860898)
