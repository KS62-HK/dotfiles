# my dotfiles

## known issue and how to fix

### Cylheim (wine)
Cylheim require dotnet 6/7, but even after installing dotnet, it still says it's missing.
Turns out they require an extra file somewhere in `/usr/`.
To fix this, put the required file in there (check their name by running cylheim in wine in terminal.)

