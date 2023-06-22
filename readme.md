# My dotfiles

## Known issues and how to fix them

### Cylheim (wine)

#### "This application requires dotnet 6"
Cylheim requires dotnet 6/7, but even after installing that, it still says dotnet is missing.\
Turns out Cylheim also requires `hostfxr.dll` in `/usr/share/dotnet/host/fxr/<dotnet version>`, in which wine is unable to write into.\
**(Side note: do not run wine with sudo for this, reason explained [here](https://wiki.winehq.org/FAQ#Should_I_run_Wine_as_root.3F))** \
To fix this, simply put `hostfxr.dll` in said directory (either by downloading it online or copying the one in `~/.wine/drive_c/Program Files/dotnet/host/fxr/<dotnet version>`).

#### Crashes after one playback
Either Cylheim or wine has a bug where Cylheim would crash after a single playback in any version higher than v2.0.1. (specifically the ones with a .exe installer)\
Currently, the only solution is to use the zipped version (v2.0.0 or v1.8.4) which does not contain this bug.

#### Constant screen flickering
No fixes as of now.
