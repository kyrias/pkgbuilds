pkgname=irker-git
pkgver=2.12.r6.gd6c1e1c
pkgrel=1

pkgdesc="IRC client daemon accepting JSON notification requests"
url="http://www.catb.org/esr/irker/"
arch=('any')
license=('BSD')

depends=('python2')
makedepends=('xmlto' 'docbook-xml' 'docbook-xsl')

source=('git+https://gitorious.org/irker/irker.git')

sha1sums=('SKIP')

pkgver() {
	cd irker
	git describe --long | sed -r 's/([^-]*-g)/r\1/; s/-/./g'
}

build() {
	cd irker
	sed -i '1s|python|python2|' irk irkerd irkerhook.py
	make
}

package() {
	cd irker
	make DESTDIR="$pkgdir" install
	install -Dm 755 irkerhook.py "$pkgdir"/usr/bin/irkerhook.py
	install -Dm 755 irk "$pkgdir"/usr/bin/irk
	install -Dm 644 COPYING "$pkgdir"/usr/share/licenses/irker/LICENSE
}
