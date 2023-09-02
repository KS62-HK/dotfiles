# My dotfiles

## Images
Coming Soon™

## Known issues and how to fix them

### Cylheim (wine)

#### "This application requires dotnet 6"

Cylheim requires dotnet (desktop) 6/7, so you should install the version it prompts you to install. (or run `winetricks dotnetdesktop6 dotnetdesktop7`)

*But,* even after installing that, it *might* still say dotnet is missing.

Turns out, Cylheim also requires `hostfxr.dll` (and potentially more files) in its dotnet directory, and if you have dotnet installed via your package manager, `wine` will default its dotnet directory to be in `/usr/share/dotnet/`. Since the linux version does not provide said dll, Cylheim reports that it can't launch.

There are three ways to fix this:

1. Put `DOTNET_ROOT="C:\Program Files\dotnet"` in `/etc/environment`. (Requires logout/reboot)
2. Add `DOTNET_ROOT="C:\Program Files\dotnet"` behind the `wine` command before executing. (e.g. `DOTNET_ROOT="C:\Program Files\dotnet" wine /path/to/Cylheim`)
3. Put the required files in `/usr/share/dotnet/host/fxr/<dotnet version>` (either by downloading it online or copying the one in `~/.wine/drive_c/Program Files/dotnet/host/fxr/<dotnet version>`).

#### Stuck on splash screen
Likely due to [this](https://bugs.winehq.org/show_bug.cgi?id=52396) `wine` bug. For now, install `wine-staging` instead of `wine` to fix this.

#### Crashes after one playback
Install `dotnet40` (or `dotdet48` if you want) with `winetricks` to fix.

#### v3.0.0?
Same as above.

#### Constant screen flickering
Seems to be the consequences of wine not yet supporting wayland [(source)](https://wiki.archlinux.org/title/wine#Xwayland_problems), maybe it doesn't happen on x11 but I don't have time to test that.

### CytoidPlayer (Wine)

#### Missing text on the buttons
You need to install the required fonts in wine first, and it seems that `winetricks corefonts` does the trick.
