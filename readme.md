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

#### ~~Crashes after one playback~~
**seems to be fixed, I have no idea how and why though.**
<details>
<summary>Old text</summary>
Either Cylheim or wine has a bug where Cylheim would crash after a single playback in any version higher than v2.0.1. (Specifically the ones with a .exe installer)
<br>
Currently, the only solution is to use the zipped version (v2.0.0 or v1.8.4) which does not contain this bug.
<br>
And before you ask. <b>No, using a 32bit wine prefix does not fix this.</b>
</details>

#### v3.0.0?
It is possible to run Cylheim v3.0.0+ after adding some files. 

Follow these steps:
1. Install a [.NET Desktop Runtime](https://dotnet.microsoft.com/en-us/download/dotnet/7.0) version that is exactly or higher than `7.0.0-preview.4`. (Alternatively run `winetricks dotnetdesktop7`)
2. Install Cylheim with the .exe file.
3. Download and put `msvcr120_clr0400.dll` in `~/.wine/drive_c/windows/system32`.
4. Download and put `wminet_utils.dll` in `~/.wine/drive_c/windows/Microsoft.NET/Framework64/<version number>`.

#### Constant screen flickering
Seems to be the consequences of wine not yet supporting wayland [(source)](https://wiki.archlinux.org/title/wine#Xwayland_problems), maybe it doesn't happen on x11 but I don't have time to test that.

### CytoidPlayer (Wine)

#### Missing text on the buttons
You need to install the required fonts in wine first, and it seems that `winetricks corefonts` does the trick.
