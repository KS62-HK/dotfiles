# My dotfiles

## Images
Coming Soon™

## Known issues and how to fix them

### Cylheim (wine)

#### "This application requires dotnet 6"

Cylheim requires dotnet 6/7, so you should install the version it prompts you to install. (Run `winetricks dotnet6 dotnet7 dotnetdesktop6 dotnetdesktop7`)\
*But,* even after installing that, it might still say dotnet is missing.

Turns out, Cylheim also requires `hostfxr.dll` in its dotnet directory, but since `wine` default its dotnet directory to be in `/usr/share/dotnet/`, and Linux does not install `hostfxr.dll` by default, Cylheim reports that it can't launch.

There are two ways to fix this:

1. Add `DOTNET_ROOT="C:\Program Files\dotnet"` behind the `wine` command before executing. (e.g. `DOTNET_ROOT="C:\Program Files\dotnet" wine /path/to/Cylheim`)
2. Put `hostfxr.dll` in `/usr/share/dotnet/host/fxr/<dotnet version>` (either by downloading it online or copying the one in `~/.wine/drive_c/Program Files/dotnet/host/fxr/<dotnet version>`).

#### Stuck on splash screen
Your wine version is too old!\
For me, Cylheim last worked on wine 8.4 and up, so you might want to upgrade to that.

#### Crashes after one playback
Either Cylheim or wine has a bug where Cylheim would crash after a single playback in any version higher than v2.0.1. (Specifically the ones with a .exe installer)\
Currently, the only solution is to use the zipped version (v2.0.0 or v1.8.4) which does not contain this bug.

#### v3.0.0?
It is possible to run Cylheim v3.0.0+ after adding some files, unfortunately this version also suffers from the problem above.

Follow these steps:
1. Install a [.NET Runtime *and* .NET Desktop Runtime](https://dotnet.microsoft.com/en-us/download/dotnet/7.0) version that is exactly or higher than `7.0.0-preview.4`.
2. Install Cylheim with the .exe file.
3. Download and put `msvcr120_clr0400.dll` in `~/.wine/drive_c/windows/system32`.
4. Download and put `wminet_utils.dll` in `~/.wine/drive_c/windows/Microsoft.NET/Framework64/<version number>`.

#### Constant screen flickering
No fixes as of now.\
(Seems to be less severe on v3.0.0+, though.)

### CytoidPlayer (Wine)

#### Missing text on the buttons
You need to install the required fonts in wine first.\
I am not sure what font it is, so I just run `winetricks allfonts` and it works.
