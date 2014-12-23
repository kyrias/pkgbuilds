pkgname=tmux-256color-it
pkgver=0.0.1
pkgrel=4

pkgdesc='Terminfo files for tmux that support italics'
url='https://theos.kyriasis.com/~kyrias'
arch=('any')
license=('GPL')

makedepends=('ncurses')

source=('http://git.savannah.gnu.org/cgit/screen.git/plain/COPYING')
sha256sums=('8ceb4b9ee5adedde47b31e975c1d90c73ad27b6b165a1dcd80c7c545eb65b903')

build() {
	infocmp -I screen-256color | sed \
	    -e 's/^screen-256color[^|]*|[^,]*,/tmux-256color-it|tmux-256color with italics support,/' \
	    -e 's/%?%p1%t;3%/%?%p1%t;7%/' \
	    -e 's/smso=[^,]*,/smso=\\E[7m,/' \
	    -e 's/rmso=[^,]*,/rmso=\\E[27m,/' \
	    -e '$s/$/ sitm=\\E[3m, ritm=\\E[23m,/' \
	    > tmux-256color-it
}

package() {
	install -d "$pkgdir"/usr/share/terminfo
	tic tmux-256color-it -o "$pkgdir"/usr/share/terminfo

	install -Dm644 COPYING "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
