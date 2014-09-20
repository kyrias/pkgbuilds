pkgname=pam-krb5
pkgver=4.6
pkgrel=1

pkgdesc='A PAM module providing Kerberos v5 support.'
url='http://www.eyrie.org/~eagle/software/pam-krb5/'
arch=('i686' 'x86_64')
license=('custom')

options=('!libtool')

depends=('krb5' 'pam')

source=(http://archives.eyrie.org/software/kerberos/pam-krb5-$pkgver.tar.gz{,.asc})

md5sums=('296e9c8281419ce1fc41d537d18f74b8'
         'c68a521345d79d54fb129a3f4ca2767b')

build() {
	cd pam-krb5-$pkgver
	./configure --prefix=/usr \
	    --enable-reduced-depends \
	    --libdir=/usr/lib
	make
}

package() {
	cd pam-krb5-$pkgver
	make DESTDIR="$pkgdir" install
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/pam-krb5/LICENSE
}
