pkgname=dex-git
pkgver=0.7.r12.g2d158ca
pkgrel=1

pkgdesc="Program to execute DesktopEntry files"
url="https://github.com/jceb/dex"
license=('GPL2')
arch=('any')

depends=('python')
makedepends=('git' 'python-sphinx')

provides=('dex')
conflicts=('dex')

source=('git+https://github.com/jceb/dex.git')

sha256sums=('SKIP')

pkgver() {
	cd dex
	git describe --tags | sed -r 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
	cd dex
	make
}

package() {
	cd dex
	install -m755 -D dex "$pkgdir"/usr/bin/dex
	install -D man/dex.1 "$pkgdir"/usr/share/man/man1/dex.1
}
