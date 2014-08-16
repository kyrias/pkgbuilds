pkgname=tmux-256color-it
pkgver=0.0.1
pkgrel=2

pkgdesc="Terminfo files for tmux that support italics."
url="https://theos.kyriasis.com/~kyrias"
arch=('any')
license=('MIT')

makedepends=('ncurses')

source=('tmux-256color-it'
        'LICENSE')
sha256sums=('58ea656c17cbedd06c386fd3b77f4a8ac3e39781799c27d9b0ab2fa15a191ee8'
            'd7c21d3e838f422c3977fe20c888e12365550a8eca5e57c944bf06a956071876')

package() {
	install -d "$pkgdir"/usr/share/terminfo
	tic tmux-256color-it -o "$pkgdir"/usr/share/terminfo

	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
