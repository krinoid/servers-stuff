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
