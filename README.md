## SSH

### Perl & Locale issues

Problem:
```
user@host:~ $ perl
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_TERMINAL = "iTerm2",
	LC_CTYPE = "UTF-8",
	LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_GB.UTF-8")
```

Solution:
- when caused by iTerm: Disable auto-locale setup (in Preferences -> Profiles -> Terminal)
- when caused by the lack of locale setup, e.g. on Debian-based os:
```bash
export LANGUAGE=en_US.UTF-8
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
export LC_CTYPE=en_US.UTF-8
```

```
$ sudo locale-gen
$ sudo dpkg-reconfigure locales 
```

References:
- https://stackoverflow.com/a/46939017
- https://stackoverflow.com/a/63717870


## Networking

### WPA Supplicant

Manually connect to wifi from the CLI, useful for debugging embedded stuff:
```
sudo wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf -i wlan0
```

Example `wpa_supplicant.conf`:
```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=US # CHANGE (radio regulation is different per country)

network={
	ssid="NETWORK_NAME"
	psk="NETWORK_PASSWORD"
}
```

## RaspberryPI

```
$ diskutil list
$ diskutil unmountDisk /dev/diskN # N -> depends on the ID that SD Card got
$ sudo dd bs=1m if=2021-05-07-raspios-buster-armhf-lite.img of=/dev/rdiskN; sync
$ sudo diskutil eject /dev/rdiskN
```

## Disks & Storage

`dd` tip: `Ctrl+T` shows progress of bytes transferred

## Language, Locale

setting `export LC_ALL=en_US.UTF-8` solves a lot of problems, e.g. related to [Perl & Locale issues](#perl--locale-issues) or issues with https://starship.rs
