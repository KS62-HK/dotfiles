# My dotfiles

## Images
Coming Soon™

## Known issues and how to fix them

### Cylheim (wine)

#### "This application requires dotnet 6"

Cylheim requires dotnet (desktop) 6/7, so you should install the version it prompts you to install. (or run `winetricks dotnetdesktop6 dotnetdesktop7`)

*But,* even after installing that, it *might* still report that dotnet is missing.

Turns out, Cylheim also requires `hostfxr.dll` (and potentially more files) in its dotnet directory, and if you have dotnet installed via your package manager, `wine` will default its dotnet directory to be in `/usr/share/dotnet/`. Since the linux version does not provide said dll, Cylheim reports that it can not be launched.

There are three ways to fix this:

1. Put `DOTNET_ROOT="C:\Program Files\dotnet"` in `/etc/environment`. (Requires logout/reboot)
2. Add `DOTNET_ROOT="C:\Program Files\dotnet"` behind the `wine` command before executing. (e.g. `DOTNET_ROOT="C:\Program Files\dotnet" wine /path/to/Cylheim`)
3. Put the required files in `/usr/share/dotnet/host/fxr/<dotnet version>` (either by downloading it online or copying the one in `~/.wine/drive_c/Program Files/dotnet/host/fxr/<dotnet version>`).

#### Crashes after one playback
Install `dotnet40` (or `dotdet48` if you want) with `winetricks` to fix. (Note that it could take a while to install due to poor comparability)

#### v3.0.0?
Same as above.

#### Constant screen flickering
Seems to be the consequences of wine not yet supporting wayland [(source)](https://wiki.archlinux.org/title/wine#Xwayland_problems), maybe it doesn't happen on x11 but I don't have time to test that.\
Currently, a workaround is to start cylheim and never change its window size upon startup.\
If you aren't sure, you can run `wine explorer /desktop=name,1920x1080 path/to/cylheim.exe` to guarantee it spawns in its default size. (You can change the `1920x1080` to your actual screen size!)

### CytoidPlayer (Wine)

#### Missing text on the buttons
You need to install the required fonts in wine first, and it seems that `winetricks corefonts` does the trick.
