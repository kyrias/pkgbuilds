pkgname=mutt-kz-git
pkgver=1.5.22.1.rc1.r32.g738df8f
pkgrel=1

pkgdesc='Small but powerful text-based mail client'
url='https://github.com/karelzak/mutt-kz'
arch=('i686' 'x86_64')
license=('GPL')

depends=('gdbm' 'gpgme' 'openssl>=0.9.8e' 'libsasl'
         'mime-types' 'ncurses' 'notmuch' 'zlib')
makedepends=('git' 'gnupg' 'libxslt')

conflicts=('mutt')
provides=('mutt')

source=('git+https://github.com/karelzak/mutt-kz.git' 'xdg.patch'
        'trash.patch::https://www.cs.oberlin.edu/~kuperman/help/code/patch-1.5.20.bk.trash_folder-purge_message.1.txt')
sha1sums=('SKIP'
          '8cbae5a7ade3812cbdcb8a8dfabb29b042b7296a'
          'b63fe4e7ea2a113819558862be1387364ec24213')

pkgver() {
	cd mutt-kz
	git describe --long | sed -E 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

prepare() {
	cd mutt-kz

	patch -p1 < "$srcdir/trash.patch"
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
	    --enable-pop \
	    --enable-smtp \
	    --with-idn \
	    --with-sasl \
	    --with-gss \
	    --with-ssl=/usr
	make
}

package() {
	cd mutt-kz

	make DESTDIR="$pkgdir" install
	rm "$pkgdir/etc/mime.types"
}
