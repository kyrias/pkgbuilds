pkgbase=termite-git
pkgname=('termite-git' 'termite-terminfo-git')
pkgver=9.r3.gcb3dfb7
pkgrel=1

pkgdesc="A simple VTE-based terminal emulator"
url="https://github.com/thestinger/termite/"
arch=('i686' 'x86_64')
license=('GPL')

depends=('atk' 'cairo' 'glibc' 'glib2' 'gcc-libs'
         'gtk3' 'pango' 'vte3-select-text-git>=0.38.0')
makedepends=('git' 'ncurses')

provides=('termite')
conflicts=('termite')

backup=('etc/xdg/termite/config')

source=('git+https://github.com/thestinger/termite'
        'git+https://github.com/thestinger/util'
        'reverse_url_search.patch')

md5sums=('SKIP'
         'SKIP'
         '8d4e4216cee58a1b0df223dde2216bf1')

pkgver() {
	cd termite
	git describe | sed 's/^v//; s/-/.r/; s/-/./'
}

prepare() {
	cd termite
	git submodule init
	git config submodule.util.url "$srcdir"/util
	git submodule update
	patch -Np1 -i "$srcdir"/reverse_url_search.patch
}

build() {
	cd termite
	make
}

package_termite-git() {
	cd termite
	make PREFIX=/usr DESTDIR="$pkgdir" install
	install -Dm644 config "$pkgdir"/etc/xdg/termite/config
}

package_termite-terminfo-git() {
	pkgdesc="terminfo for termite-git, a simple VTE-based terminal emulator"
	depends=()

	install -d "$pkgdir"/usr/share/terminfo
	tic -x "$srcdir"/termite/termite.terminfo -o "$pkgdir"/usr/share/terminfo
}
