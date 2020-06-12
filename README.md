<h1 align="center">
  <img src="data/icons/scalable/apps/com.github.nahuelwexd.Replay.svg"/>
  <br>
  Replay
</h1>
<p align="center">An open source YouTube client for GNOME.</p>
<p align="center">
  <a href="https://github.com/nahuelwexd/replay/actions">
    <img alt="Continuous Integration" src="https://github.com/nahuelwexd/replay/workflows/Continuous%20Integration/badge.svg"/>
  </a>
  <a href="https://stopthemingmy.app">
    <img alt="Please do not theme this app" src="https://stopthemingmy.app/badge.svg"/>
  </a>
  <a href="COPYING">
    <img alt="License" src="https://img.shields.io/github/license/nahuelwexd/replay?label=License&logo=gnu"/>
  </a>
<p>
<p align="center">
  <img alt="UI Concept" src="ui-concept.png"/>
</p>

Replay is a brand new app for GNOME, designed to be a faster and bulletproof
YouTube client for laptops and phones. You would be able to manage all your
suscriptions and playlists, search for videos and explore the new trendings for
your location (or other locations).

**This project is still under active development, and not yet ready for use.**

## Install

### Stable

Since this project is still under active development, there's no current stable
build. You will see a Flathub link here when there's one 🙂️

### Development

Development builds are automatically generated every time a new change occurs in
this repository, and are marked with a custom icon and style. You can install a
development build simply by going to the [actions](https://github.com/nahuelwexd/replay/actions)
tab of this repository, and downloading one of those that have been successfully
generated.

> **NOTE:** You must download the artifact called "Flatpak Bundles", which
contains 2 flatpak files ready to install: the application and the locales

## Build

You want to build this project and maybe contribute to it? Well, this is the
right guide for you. But first, you will need to get an API key for the YouTube
Data API v3. Go to the [Google Developers Console](https://console.console.developers.google.com),
create a new project and get a new API key, then choose the way you want to go
to build the app: GNOME Builder or manually.

### GNOME Builder

The GNOME Builder way is easier than any other, and it's the recommended one.
You just need to:

- Open GNOME Builder (If you haven't installed GNOME Builder yet, do it from your
  distro repos or from [Flathub](https://flathub.org/apps/details/org.gnome.Builder)!)
- Click on the "Clone repository" button
- Paste the link to this repo and clone it
- Open the terminal integrated with GNOME Builder, and enter the following
  command:

  ```shell
  chmod +x build-aux/generate-replay-constants.vala
  ./build-aux/generate-replay-constants.vala API_KEY src/constants.vala
  ```

  Where you need to replace `API_KEY` with the API key you get in the Google
  Developers Console.

- Hit the "Run" button (▶)

GNOME Builder would automatically download and install all the needed dependencies,
build the app and run it. Then you can export it as a bundle in order to install
it in your system.

### Manually

You will need to download and install all of these dependencies:

- `glib-2.0`
- `gobject-2.0`
- `gee-0.8`
- `gio-2.0`
- `libsoup-2.4`
- `gtk+-3.0`
- `libhandy-1`
- `gjson-1.0`
- `sassc`
- `meson`
- `vala`
- `git` (this is obvious, but still)

Then run these commands on your preferred terminal emulator:

```shell
git clone https://github.com/nahuelwexd/replay.git
cd replay
chmod +x build-aux/generate-replay-constants.vala
./build-aux/generate-replay-constants.vala API_KEY src/constants.vala
meson build --buildtype plain
ninja -C build install
```

Where `API_KEY` should be replaced with the API key you get on the Google
Developers Console.

## License

This project is licensed under the [GNU General Public License v3](COPYING) or
any later version.

[tl;dr](https://www.tldrlegal.com/l/gpl-3.0): You may copy, distribute and modify
this app as long as you track changes/dates in source files. Any modifications to
GPL-licensed code must also be available under the GPL along with build & install
instructions.
