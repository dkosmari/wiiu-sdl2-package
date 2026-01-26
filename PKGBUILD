_pkgname=SDL
_branch=wiiu-sdl2-devel
pkgname=wiiu-sdl2-dkosmari
conflicts=('wiiu-sdl2')
provides=('wiiu-sdl2')
pkgver=2.28.5
pkgrel=3
pkgdesc="The Simple DirectMedia Layer (SDL) library, version 2."
arch=('any')
url="https://libsdl.org"
license=("LGPL")
options=(!buildflags !strip staticlibs)
makedepends=(
    'wiiu-pkg-config'
    'dkp-toolchain-vars'
)
depends=(
    'wut'
)

source=("${_pkgname}::git+https://github.com/dkosmari/SDL.git#branch=${_branch}")
groups=('wiiu-portlibs' 'wiiu-sdl2-libs')

build() {
    cd "${srcdir}/${_pkgname}"
    
    ${DEVKITPRO}/portlibs/wiiu/bin/powerpc-eabi-cmake \
        -S. \
        -Bbuild \
        -DCMAKE_VERBOSE_MAKEFILE=ON \
        -DCMAKE_BUILD_TYPE="Release" \
        -DCMAKE_INSTALL_PREFIX=${DEVKITPRO}/portlibs/wiiu \
        -DCMAKE_C_FLAGS_RELEASE="-g -Os -DNDEBUG" \
        -DCMAKE_CXX_FLAGS_RELEASE="-g -Os -DNDEBUG"

    make -C build
}

package() {
    cd "${srcdir}/${_pkgname}"

    make -C build install DESTDIR="${pkgdir}"
}

sha256sums=('SKIP')
