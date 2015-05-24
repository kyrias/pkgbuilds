pkgname=tty-solitaire-git
pkgver=0.2.0
pkgrel=1

pkgdesc='An ncurses-based Klondike solitaire clone'
url='https://github.com/mpereira/tty-solitaire'
arch=('i686' 'x86_64')
license=('MIT')

makedepends=('git')
depends=('ncurses')

source=('git+https://github.com/mpereira/tty-solitaire')

sha256sums=('SKIP')

pkgver() {
	cd tty-solitaire
	git describe --tags | sed 's/^v//; s/-/.r/; s/-/./'
}

build() {
	cd tty-solitaire
	make
}

package() {
	cd tty-solitaire
	make DESTDIR="$pkgdir" PREFIX="/usr" install
}
