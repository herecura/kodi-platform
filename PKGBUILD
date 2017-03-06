# $Id$
# Maintainer: BlackEagle <ike.devolder@gmail.com>>

pkgname=kodi-platform
_commit=36fb493
pkgver=20170306.36fb493
pkgrel=1
pkgdesc="platform library for external kodi addons"
arch=('i686' 'x86_64')
url='https://github.com/xbmc/kodi-platform'
license=('GPL')
depends=('kodi' 'p8-platform')
makedepends=('git' 'cmake' 'kodi-dev')
source=("$pkgname::git://github.com/xbmc/kodi-platform.git#commit=$_commit")
sha256sums=('SKIP')

pkgver() {
	cd "$pkgname"
	git log -1 --date=short --format="%cd.%h" | tr -d '-'
}

build() {
	cd "$pkgname"
	cmake \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_BUILD_TYPE=Release \
		-DBUILD_SHARED_LIBS=1 \
		-DUSE_LTO=1
	make
}

package() {
	cd "$pkgname"
	make DESTDIR="$pkgdir/" install
}

