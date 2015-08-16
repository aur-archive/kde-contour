# Maintainer: Tobias Hunger <tobias dot hunger at gmx dot de>
pkgname=kde-contour
pkgver=20110814
pkgrel=1
pkgdesc="Context sensitive user interface for Plasma Active"
arch=(i686 x86_64)
url="http://community.kde.org/Plasma/Active/Contour"
license=('LGPL')
groups=()
depends=()
makedepends=('cmake' 'git' 'kde-plasma-mobile-git' 'qt-mobility-git')
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=()
noextract=()
md5sums=() #generate with 'makepkg -g'

_gitroot=git://anongit.kde.org/contour
_gitname=contour

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"

  msg "Starting build..."
  mkdir "$srcdir/build" > /dev/null 2>&1 || true
  cd "$srcdir/build"

  cmake "$srcdir/$_gitname" \
      -DCMAKE_BUILD_TYPE=debugfull \
      -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd "$srcdir/build"
  make DESTDIR="$pkgdir/" install
}

