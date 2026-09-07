# OG-os-repo

Pacman repository for OG-OS's own desktop suite (og-bar, og-settings,
og-files, og-search, og-clip, og-notify, og-notif-center, og-apps,
og-links, og-scripts). Hosted via GitHub Pages so an installed OG-OS
system can actually receive updates after install — see
[OG-toolkit/distro](https://github.com/OmegaGiven/OG-toolkit/tree/main/distro)
for the build tooling and the ISO this repo feeds.

## Using this repo

Add to `/etc/pacman.conf`:

```ini
[ogos]
SigLevel = Optional TrustAll
Server = https://omegagiven.github.io/OG-os-repo/x86_64
```

Then `sudo pacman -Sy`. This is what `install-ogos.sh` sets up
automatically on a fresh install.

## Trust model

`SigLevel = Optional TrustAll` — packages here are unsigned. This is a
single-maintainer repo built on a personal machine, not a
multi-contributor project; GPG package signing is a real gap for a
distro anyone else installs and is tracked as follow-up work, not
silently ignored. Until then, treat this the way you'd treat any
unsigned third-party repo: it's exactly as trustworthy as
`https://github.com/OmegaGiven/OG-toolkit`'s source is.

## Publishing

Packages are built and published from the dev machine via
`OG-toolkit/distro/pkgbuilds/publish.sh` — see that script for the
build → repo-add → push pipeline. Not automated CI (yet); a manual
step run after committing app changes worth shipping.
