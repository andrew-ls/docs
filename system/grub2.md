# GRUB 2

## Configuring

The base configuration for GRUB is located at `/etc/default/grub`. This file is
sourced when `grub2-mkconfig` is building the GRUB configuration.

[Various variables](https://www.gnu.org/software/grub/manual/grub/grub.html#Configuration)
can be defined in POSIX shell syntax to configure GRUB. Of these variables, `GRUB_CMDLINE_LINUX` is notable for defining the parameters passed to the Linux
kernel on startup.

The following is an example of a `GRUB_CMDLINE_LINUX` with two Linux kernel
parameters set:

````````````````````````````````````````````````````````````````````````````` sh
GRUB_CMDLINE_LINUX="rhgb quiet"
````````````````````````````````````````````````````````````````````````````````

There are many other
[Linux kernel parameters](https://www.kernel.org/doc/html/latest/admin-guide/kernel-parameters.html)
than can be used in this way; of particular note is the `resume` parameter,
defining the device the kernel will check for hibernation state data. There are
several ways of defining the device: the most common are plain `/dev/…` paths
and partition UUIDs (with the `UUID` or `PARTUUID` specifiers).

> Partition `UUID`s and `PARTUUID`s can be found using the `blkid` utility.

The following are examples of settings for `resume`:

`````````````````````````````````````````````````````````````````````````` linux
resume=/dev/sda2
resume=UUID=dec16753-26c5-4317-983b-848b8da58d1a
resume=PARTUUID=1a9c5486-21cf-480e-add5-b8eae9e9e4e7
````````````````````````````````````````````````````````````````````````````````

## Building

Building the GRUB configuration is achieved with the `grub2-mkconfig`. To build,
simply call `grub2-mkconfig -o [PATH]` with root privileges, where `[PATH]` is
the path to the GRUB configuration for your system. The base configuration in
`/etc/default/grub` will then be integrated into the system configuration.

On a [Fedora UEFI system](https://docs.fedoraproject.org/en-US/quick-docs/bootloading-with-grub2/#create-a-grub-2-configuration),
the command would be:

````````````````````````````````````````````````````````````````````````````` sh
grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
````````````````````````````````````````````````````````````````````````````````
