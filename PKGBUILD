pkgname=dunst-git
pkgver=1.0.0.616.9117df5
pkgrel=1

pkgdesc="Customizable and lightweight notification-daemon"
url="http://www.knopwob.org/dunst"
arch=('i686' 'x86_64')
license=('BSD')

depends=('libxinerama' 'libxss' 'pango' 'libnotify')
makedepends=('git' 'perl')

provides=('dunst' 'notification-daemon')
conflicts=('dunst')

source=('git://github.com/knopwob/dunst.git')

sha256sums=('SKIP')

pkgver() {
	cd dunst
	git describe | sed -r 's/^v//; s/([^-]*-g)/r\1/; s/znc-//; s/-/./g'
}

build() {
	cd dunst
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 dunstify
}

package() {
	cd dunst
	make DESTDIR="${pkgdir}" PREFIX=/usr install

	install -Dm755 dunstify "$pkgdir"/usr/bin/dunstify
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/"$pkgname"/LICENSE
}
