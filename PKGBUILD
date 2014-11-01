pkgname=isync-git
pkgver=1.2.0.r651.f377e7b
pkgrel=1

pkgdesc="IMAP mail synchronizer for offline/batch mail editing"
url="http://isync.sourceforge.net"
arch=('i686' 'x86_64')
license=('GPL')

conflicts=('isync')
replaces=('isync')

depends=('openssl' 'libsasl' 'cyrus-sasl-gssapi')
makedepends=('perl-timedate')

source=('git://git.code.sf.net/p/isync/isync')

sha256sums=('SKIP')

pkgver() {
	cd isync
	echo $(grep -m 1 -o -E "[0-9.]*" configure.ac)'.r'$(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

prepare() {
	cd isync
	./autogen.sh
}

build() {
	cd isync
	./configure --prefix=/usr --with-sasl=/usr/lib/sasl2
	make
}

package() {
	cd isync
	make DESTDIR="$pkgdir" install
}
