pkgname=j4-dmenu-desktop-git
pkgver=r2.11.r9.gb4ce0c7
pkgrel=1

pkgdesc="A rewrite of i3-dmenu-desktop, which is much faster"
url="https://github.com/enkore/j4-dmenu-desktop"
arch=('i686' 'x86_64')
license=('GPL3')

depends=('dmenu')
makedepends=('git' 'cmake')

provides=('j4-dmenu-desktop')
conflicts=('j4-dmenu-desktop')

source=('git+https://github.com/enkore/j4-dmenu-desktop')
md5sums=('SKIP')

pkgver() {
	cd j4-dmenu-desktop
	git describe | sed -E 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
	cd j4-dmenu-desktop
	cmake -DCMAKE_INSTALL_PREFIX=/usr -DNO_TESTS=1 .
	make
}

package() {
	cd j4-dmenu-desktop
	make DESTDIR="$pkgdir" install
}
