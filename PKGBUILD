pkgname=opensmtpd-ldap
pkgver=5.4.2p1
pkgrel=2

pkgdesc='Free implementation of the server-side SMTP protocol'
url='http://www.opensmtpd.org/'
arch=('i686' 'x86_64')
license=('custom')

options=('emptydirs')

depends=('libevent' 'openssl')

provides=('smtp-server' 'smtp-forwarder')
conflicts=('smtp-server' 'smtp-forwarder')

backup=('etc/smtpd/smtpd.conf' 'etc/smtpd/aliases')

install=opensmtpd.install
source=("http://www.opensmtpd.org/archives/opensmtpd-$pkgver.tar.gz"
        'smtpd.service'
        'smtpd.socket')

md5sums=('c76b39a5fcc0ad05eea541e74b16e62a'
        'a278f272d97a9fe5a8aac784a7c98d67'
        'c2c01e9ca78df3f65efe40a7c0e17ee0')

prepare() {
	sed -ri 's,/etc/mail,/etc/smtpd,g' "opensmtpd-$pkgver/smtpd/smtpd.conf"
}

build() {
	cd opensmtpd-$pkgver

	# Remove _FORTIFY_SOURCES: FS#38124
	export CPPFLAGS=''
	./configure \
	    --prefix=/usr \
	    --sysconfdir=/etc/smtpd \
	    --sbindir=/usr/bin \
	    --libexecdir=/usr/lib/smtpd \
	    --with-maildir=/var/spool/mail \
	    --with-privsep-path=/var/empty \
	    --with-sock-dir=/run \
	    --with-ca-file=/etc/ssl/certs/ca-certificates.crt \
	    --with-privsep-user=smtpd \
	    --with-queue-user=smtpq \
	    --with-experimental-ldap \
	    --with-pam

	make
}

package() {
	cd opensmtpd-$pkgver

	make DESTDIR="$pkgdir" install

	# install license and systemd unit files
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
	install -Dm644 "$srcdir/smtpd.service" "$pkgdir/usr/lib/systemd/system/smtpd.service"
	install -Dm644 "$srcdir/smtpd.socket" "$pkgdir/usr/lib/systemd/system/smtpd.socket"

	# install an empty aliases file (used by the default config)
	install -Dm644 /dev/null "$pkgdir/etc/smtpd/aliases"
}
