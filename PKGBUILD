pkgname=tmux-256color-it
pkgver=0.0.2
pkgrel=1

pkgdesc="Terminfo files for tmux that support italics."
url="https://theos.kyriasis.com/~kyrias"
arch=('any')
license=('MIT')

makedepends=('ncurses')

source=('tmux-256color-it'
        'LICENSE')
sha256sums=('cb19b5bbe3155165a5f3d0ce2ea7bc267611244d871050000b9d98d971cec70b'
            'd7c21d3e838f422c3977fe20c888e12365550a8eca5e57c944bf06a956071876')

package() {
	install -d "$pkgdir"/usr/share/terminfo
	tic tmux-256color-it -o "$pkgdir"/usr/share/terminfo

	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
