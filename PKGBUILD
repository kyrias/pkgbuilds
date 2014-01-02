# Maintainer: Tom <tomgparchaur@gmail.com>
# Contributor: Johannes Löthberg <johannes@kyriasis.com>
# Based on a quantax contribution for irssi-otr

pkgname=xchat-otr
pkgver=0.3
pkgrel=2
pkgdesc="Off-the-Record Messaging (OTR) plugin for the XChat IRC client"
arch=('i686' 'x86_64')
url="http://irssi-otr.tuxfamily.org/"
license=('GPL2')
depends=('xchat' 'libotr3')
makedepends=('cmake' 'pkgconfig' 'python')
source=("http://download.tuxfamily.org/irssiotr/${pkgname}-${pkgver}.tar.gz"
		'http://xchat.org/docs/xchat-plugin.h')
md5sums=('49706959af491c721a8a5a62bd224670'
		 '5ee7da5abedc78a30b90e737370d8f0b')

build() {
	cd xchat-otr-$pkgver
	mkdir -p xchat
	install -m 644 "$srcdir"/xchat-plugin.h xchat/
	find . -type f -print0 | xargs -0 sed -i 's|libotr|libotr3|g'
	cmake -DCMAKE_INSTALL_PREFIX=/usr . -DLIBOTR_LIBRARY=/usr/lib/libotr3.so
	make
}

package(){
	cd xchat-otr-$pkgver
	make DESTDIR="$pkgdir" install
	mv "$pkgdir"/usr/share/doc/irssi-otr "$pkgdir"/usr/share/doc/xchat-otr
	install -m 644 README.xchat ${pkgdir}/usr/share/doc/xchat-otr
}

# vim: set ts=4 sw=4 noet:
