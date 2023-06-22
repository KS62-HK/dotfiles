# My dotfiles

## known issues and how to fix them

### Cylheim (wine)

#### "This application requires dotnet 6"
Cylheim require dotnet 6/7, but even after installing dotnet, it still says it's missing.  
Turns out they require an extra file somewhere in `/usr/`.  
To fix this, put the required file in there (check their name by running cylheim in wine in terminal.)

#### Crashes after one playback
Either Cylheim or wine has a bug where Cylheim would crash after a single playback in any version higher than v2.0.1. (specifically the ones with a .exe installer)  
Currently, the only solution is to use the zipped version (v2.0.0 or v1.8.4) which does not contain this bug.

#### Constant screen flickering
No fixes as of now.
