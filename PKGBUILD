pkgname=cower-git
pkgver=11.r22.g0c32b94
pkgrel=1

pkgdesc="A simple AUR agent with a pretentious name"
url="http://github.com/falconindy/cower"
arch=('i686' 'x86_64')
license=('MIT')

depends=('curl' 'pacman' 'yajl' )
makedepends=('git' 'perl')

conflicts=('cower')
provides=('cower')

source=("git://github.com/falconindy/cower")
md5sums=('SKIP')

pkgver() {
	cd 'cower'
	git describe --long | sed -E 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
	make -C cower
}

package() {
	make -C cower PREFIX=/usr DESTDIR="$pkgdir" install
}

