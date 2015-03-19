pkgname=yalc-git
pkgver=0.0.1.rc1.r9.g2bfd6fd
pkgrel=1

pkgdesc='Yet Another LolCat'
url='https://github.com/yabok/yalc'
arch=('i686' 'x86_64')
license=('GPL')

makedepends=('git' 'cmake')

source=('git+https://github.com/yabok/yalc')

sha1sums=('SKIP')

pkgver() {
	cd yalc
	git describe --long | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
	cd yalc
	make
}

package() {
	install -Dm755 yalc/yalc "$pkgdir"/usr/bin/yalc
}
