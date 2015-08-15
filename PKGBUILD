# Maintainer: bloodredfrog <bloodredfrog@gmail.com>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>, William Rea <sillywilly@gmail.com>

pkgname=fbreader-gtk
pkgver=0.12.10
pkgrel=1
pkgdesc="An e-book reader for Linux. Old GTK+ version"
arch=('i686' 'x86_64')
url="http://www.fbreader.org/"
license=('GPL')
depends=('fribidi' 'bzip2' 'curl' 'gtk2' 'liblinebreak' 'sqlite3')
provides=('fbreader')
source=(http://www.fbreader.org/files/sources/fbreader-sources-$pkgver.tgz
	build-fix.patch)
md5sums=('da9ec4721efdb0ec0aaa182bff16ad82'
         '66ac17d8640625b6d2a806de4aa4e76c')

build() {
  export CPPFLAGS="-I/usr/include/cairo"
  export TARGET_ARCH=desktop
  export UI_TYPE=gtk
  export TARGET_STATUS=release
  export srcdir

  cd $srcdir/fbreader-$pkgver
  patch -p0 makefiles/config.mk <$srcdir/build-fix.patch
  sed -i 's#Library::Library &Library::Instance()#Library \&Library::Instance()#' fbreader/src/library/Library.cpp
  make INSTALLDIR=/usr
  make INSTALLDIR=/usr DESTDIR=$pkgdir install
}
