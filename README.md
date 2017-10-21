# qfactor

**qfactor** is a collection of CLI programs that add missing features to XQuartz and the Quartz WM.


## Warning

**This is alpha-quality software.** If you don’t know what this means, do not use any of the scripts in this collection.

If you do use qfactor, be advised that it is largely untested.


## System requirements

- To use the programs in qfactor, you need OS&nbsp;X 10.11 El Capitan, macOS 10.12 Sierra, macOS 10.13 High&nbsp;Sierra, or a later macOS version.

- Because qfactor is an addition to XQuartz, it needs XQuartz to be installed.

- As qfactor is still in alpha stage, it requires the XQuartz.app to be run on a German macOS. (For other localizations, pull requests are welcome.)

- For **qreload,** accessibility features (aka Universal Access) need to be enabled in the _Security_ System Preferences pane, and granted to every app from which qreload will be launched (e.&nbsp;g. Terminal.app).


## Installation

1. Make sure you have [Homebrew](https://brew.sh) installed.

2. Run `brew tap claui/public` if you haven’t already done so.

3. Run:

```
brew install qfactor
```


## qreload

Right now, qfactor ships with just a single program, `qreload`.

`qreload` solves the problem that whenever you change XQuartz preferences programmatically (i.&nbsp;e. using `defaults write org.macosforge.xquartz.X11`), XQuartz will not pick up the changes until you restart the app.

By simulating actions on the X11 Preferences dialog via AppleScript and the _System Events_ app, `qreload` forces XQuartz to reload the preferences from its domain while it is running.


### Usage example

This example requires XQuartz to be running.

Open a Terminal window and run the following command line to change one of X11’s configuration settings:

```
$ defaults write org.macosforge.xquartz.X11 \
    sync_clipboard_to_pasteboard -bool false
```

You will notice that the change hasn’t taken effect yet.

To coerce XQuartz into picking up the changed setting, run:

```
$ qreload
```


## License

Copyright (c) 2017 Claudia <clau@tiqua.de>

Permission to use, copy, modify, and/or distribute this software for
any purpose with or without fee is hereby granted, provided that the
above copyright notice and this permission notice appear in all
copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL
WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE
AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL
DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR
PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER
TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR
PERFORMANCE OF THIS SOFTWARE.
