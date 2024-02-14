PicomX
=====

[__picom__](https://github.com/yshui/picom) is a compositor for X, and a [fork of Compton](History.md).

**This is a development branch, bugs to be expected**

You can leave your feedback or thoughts in the [discussion tab](https://github.com/X3ric/picom/discussions).

## Features

Animation Tag working (tested on awesome wm) "work in progress" gets "_NET_NUMBER_OF_DESKTOP" and "_NET_CURRENT_DESKTOP" of the root xprop.

animation-for-menu-windows = animation for dock type.

## Problems

To use shader-fg i recommend to exclude the window from animations because is not working when animating.

To view unmap animation mantain fade true if you want to remove the fade set fade-in-step/fade-out-step to 1 .

Picom tag anim is not working always as expected.

### Dependencies

Assuming you already have all the usual building tools installed (e.g. gcc, python, meson, ninja, etc.), you still need:

* libx11
* libx11-xcb
* libXext
* xproto
* xcb
* xcb-util
* xcb-damage
* xcb-dpms
* xcb-xfixes
* xcb-shape
* xcb-renderutil
* xcb-render
* xcb-randr
* xcb-composite
* xcb-image
* xcb-present
* xcb-glx
* pixman
* libdbus (optional, disable with the `-Ddbus=false` meson configure flag)
* libconfig (optional, disable with the `-Dconfig_file=false` meson configure flag)
* libGL, libEGL (optional, disable with the `-Dopengl=false` meson configure flag)
* libpcre2 (optional, disable with the `-Dregex=false` meson configure flag)
* libev
* uthash

### To install on arch

<pre>
curl -s https://raw.githubusercontent.com/X3ric/picom/next/install | bash
</pre>

### To install on others

```meson setup --buildtype=release . build && ninja -C build/ && ninja -C build install``` in the repo dir.

## Licensing

picom is free software, made available under the [MIT](LICENSES/MIT) and [MPL-2.0](LICENSES/MPL-2.0) software
licenses. See the individual source files for details.
