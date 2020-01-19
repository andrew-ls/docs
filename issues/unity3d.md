# Unity

## Linux

### Unity Editor fails to launch

Despite being distributed through the Unity Hub AppImage, Unity Editor needs
certain optional system packages to be installed.

- On Debian family distributions, install `libgconf-2-4`.
- On Red Hat family distributions, install `mesa-libGLU`.

### Console reports `Curl error 77: Error reading ca cert file from /etc/ssl/certs/ca-certificates.crt`" error`

This occurs because Unity is hardcoded to look for certificate authorities in a
location that differs by distribution. Creating a symbolic link to the correct
location will fix the issue.

- On Fedora, execute `ln -s ca-bundle.crt /etc/ssl/certs/ca-certificates.crt`
  with root privileges.
- On openSUSE, execute `ln -s ../ca-bundle.pem /etc/ssl/certs/ca-certificates.crt`
  with root privileges.
