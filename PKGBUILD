pkgname=yawa-git
pkgver=0.9.0.r18.g31af564
pkgrel=1

pkgdesc='A tool which allows you to compose wallpapers for X.'
url='http://git.kyriasis.com/kyrias/yawa/about/'
arch=('i686' 'x86_64')
license=('GPL')

depends=('imlib2' 'libx11' 'libbsd')
makedepends=('git' 'python-sphinx' 'cmake' 'clang')

source=('git+http://git.kyriasis.com/kyrias/yawa')

sha1sums=('SKIP')

pkgver() {
	cd yawa
	git describe --long | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
	mkdir build
	cd build

	cmake -g 'Unix Makefiles' "$srcdir"/yawa -DCMAKE_INSTALL_PREFIX=/usr
	make
}

package() {
	cd build
	make DESTDIR="$pkgdir" install
}
