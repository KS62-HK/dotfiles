# My dotfiles

## Images
Coming Soon™

## Known issues and how to fix them

### Cylheim (wine)

#### "This application requires dotnet 6"
Cylheim requires dotnet 6/7, so you should install the version it prompts you to install. (via wine of cause)\
*But,* even after installing that, it might still says dotnet is missing.\

Turns out Cylheim also requires `hostfxr.dll` in `/usr/share/dotnet/host/fxr/<dotnet version>`, in which wine is unable to write into. (or maybe it's the one installed from your package manager, I am not sure)\
**(Side note: do not run wine with sudo for this, reason explained [here](https://wiki.winehq.org/FAQ#Should_I_run_Wine_as_root.3F).)** \

To fix this, simply put `hostfxr.dll` in said directory (either by downloading it online or copying the one in `~/.wine/drive_c/Program Files/dotnet/host/fxr/<dotnet version>`).\

Note that Cylheim could stop working again when a dotnet upgrade is installed, you should be able to fix it by repeating this section.

#### Stuck on splash screen
Your wine version is too old!\
For me, Cylheim last worked on wine 8.4 and up so you might want to upgrade to that.

#### Crashes after one playback
Either Cylheim or wine has a bug where Cylheim would crash after a single playback in any version higher than v2.0.1. (Specifically the ones with a .exe installer)\
Currently, the only solution is to use the zipped version (v2.0.0 or v1.8.4) which does not contain this bug.

#### Constant screen flickering
No fixes as of now.

### CytoidPlayer (Wine)

#### Missing text on the buttons
You need to install the required fonts in wine first.\
I am not sure what font it is so I just run `winetricks allfonts` and it works.
