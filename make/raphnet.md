# Raphnet adapter management tools

## Compiling

### Dependencies

The README for the repository lists dependencies as Debian packages. The
following shows the respective Fedora package for each dependency:

#### Base

* `libhidapi-dev`: `hidapi-devel`
* `libhidapi-hidraw0`: `hidapi`
* `pkg-config`: `pkgconf-pkg-config`

#### GUI

* `libgtk-3-dev`: `gtk3-devel`
* `libxml2-utils`: `libxml2`

#### GUI (runtime)

* `dfu-programmer`: `dfu-programmer`

## udev rules

Under Linux it is not possible to communicate with the devices without the
appropriate udev rules. Running the following in the root of the repository will
add said rules and restart udev:

````````````````````````````````````````````````````````````````````````````` sh
cd scripts
sudo cp 10-atmel-dfu.rules 10-raphnet.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules && sudo udevadm trigger
````````````````````````````````````````````````````````````````````````````````
