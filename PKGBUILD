# Maintainer:  Dave Murphy <davem@devkitpro.org>

pkgname=wiiu-sdl2
pkgver=2.28.5
pkgrel=2
pkgdesc="A library for portable low-level access to a video framebuffer, audio output, mouse, and keyboard"
arch=('any')
url="https://libsdl.org"
license=("LGPL")
options=(!strip libtool staticlibs)
makedepends=('wiiu-pkg-config' 'dkp-toolchain-vars')
depends=('wut')
source=("${url}/release/SDL2-${pkgver}.tar.gz"
        "wiiu-SDL2-${pkgver}.patch")
groups=('wiiu-portlibs' 'wiiu-sdl2-libs')

build() {
  cd SDL2-$pkgver
  patch -p1 -i $srcdir/wiiu-SDL2-${pkgver}.patch
  mkdir build
  cd build
  /opt/devkitpro/portlibs/wiiu/bin/powerpc-eabi-cmake .. \
    -DCMAKE_BUILD_TYPE="Release" \
    -DCMAKE_INSTALL_PREFIX=/opt/devkitpro/portlibs/wiiu \
    -DCMAKE_C_FLAGS_RELEASE="-g -Os -DNDEBUG" \
    -DCMAKE_CXX_FLAGS_RELEASE="-g -Os -DNDEBUG"
  make
}

package() {

  cd SDL2-$pkgver/build
  make install DESTDIR=$pkgdir

}

sha256sums=('332cb37d0be20cb9541739c61f79bae5a477427d79ae85e352089afdaf6666e4'
            '1794dd5d054750be90fbb5272da05ce1ace5250a1889a82c303628c5a7ac9b99')
