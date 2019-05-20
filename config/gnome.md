# GNOME

## Fractional Scaling (Wayland)

GNOME on Wayland supports fractional scaling, however the option is currently
hidden behind an experimental `dconf` setting. To enable it, execute the
following in a shell:

````````````````````````````````````````````````````````````````````````````` sh
gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
````````````````````````````````````````````````````````````````````````````````
