pkgname=mutt-kz-git
pkgver=1.5.23.1.r0.g3bbcc84
pkgrel=3

pkgdesc='Small but powerful text-based mail client'
url='https://github.com/karelzak/mutt-kz'
arch=('i686' 'x86_64')
license=('GPL')

depends=('gdbm' 'gpgme' 'openssl' 'libsasl' 'libidn'
         'mime-types' 'ncurses' 'zlib' 'notmuch-runtime')
makedepends=('git' 'gnupg' 'libxslt')

conflicts=('mutt')
provides=('mutt')

options=(strip debug)

source=('git+https://github.com/karelzak/mutt-kz.git' 'xdg.patch')

sha1sums=('SKIP'
          '8cbae5a7ade3812cbdcb8a8dfabb29b042b7296a')

pkgver() {
	cd mutt-kz
	git describe --long | sed -E 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

prepare() {
	cd mutt-kz

	patch -p1 < "$srcdir/xdg.patch"
}

build() {
	cd mutt-kz

	./prepare \
	    --prefix=/usr \
	    --sysconfdir=/etc \
	    --enable-debug \
	    --enable-gpgme \
	    --enable-hcache \
	    --enable-imap \
	    --enable-notmuch \
	    --enable-pgp \
	    --enable-smtp \
	    --with-gss \
	    --with-idn \
	    --with-sasl \
	    --with-ssl=/usr

	make
}

package() {
	cd mutt-kz

	make DESTDIR="$pkgdir" install
	rm "$pkgdir/etc/mime.types"
}
