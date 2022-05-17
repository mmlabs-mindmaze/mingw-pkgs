# pacman packaging files

This contains the required files to create the pacman packages for
libraries or program not packaged in MSYS2.

## howto

*This asserts that the sources for non public program (accessible only from
MindMaze) will be located in $MMSRCS/<package>* ie. "$MMSRCS/mmlib",
"$MMSRCS/mmpack" for the program developed by MindMaze. If the environment
variable MMSRCS is not set, it assumes to be $HOME/sources.

To create a pacman package, move to the folder containing the PKGBUILD file,
the makepkg command will copy the sources, build local-install, and create
an archive.

``` bash
# move to pacman's mmlib folder
cd mmlib

# create mingw64 pacman's mmlib package
MINGW_ARCH=mingw64 makepkg-mingw --syncdeps --log  --force

# peek into the generated package
tar tvf mingw-w64-x86_64-libmmlib0-0.3.4-1-x86_64.pkg.tar.xz

# install the result locally
pacman -U mingw-w64-x86_64-libmmlib0-0.3.4-1-x86_64.pkg.tar.xz

# check that it is installed
pacman -Qqe | grep mmlib

# remove/uninstall the package
pacman -R mingw-w64-x86_64-libmmlib0
``` 
