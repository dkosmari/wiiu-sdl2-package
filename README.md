# Alternative SDL2 package for the Wii U

This repository has binary packages for
[this SDL2 fork](https://github.com/dkosmari/SDL/tree/wiiu-sdl2-devel).

It has experimental PRs not (yet) present on the official devkitPro repository.

## Package name

This package conflicts with the official SDL2 package. You can only have one of the two
installed. Pacman will take care of the conflict and uninstall the other version, so you
don't have to do anything, other than confirming the removal of the conflicting package.

The `-dkosmari` suffix is there to make it clear it's not the official package.
