# Contributor: Pizon <pizon@pizon.org>
# Contributor: Francesco Colista <francesco.colista@gmail.com>

pkgname=dkimproxy
pkgver=1.4.1
pkgrel=4

pkgdesc="An SMTP-proxy that signs and/or verifies emails, using the Mail::DKIM module."
arch=('i686' 'x86_64')
url="http://dkimproxy.sourceforge.net/"
license=('GPL')

depends=('perl-mail-dkim' 'perl-net-server' 'perl-error')
options=('!emptydirs')

install=$pkgname.install
source=("http://downloads.sourceforge.net/$pkgname/$pkgname-$pkgver.tar.gz"
		dkimproxy_in.service dkimproxy_out.service)

sha256sums=('e5345a1d3cefd32d1fb0face9fa73490118132767253b0ce643463f1e86185bd'
			'aee1890b21ef326ac4691a73f46508319c428f2b1f618ec64e9ccbc4b95f8844'
			'5ec4cd130e0cf55ae9b548f76ee7d1ca615592f651152dcfd984a7bcdbbfd7d6')

build() {
	cd dkimproxy-$pkgver
	./configure --prefix=/usr --sysconfdir=/etc/dkimproxy
	make
}

package() {
	cd dkimproxy-$pkgver
	make install DESTDIR="$pkgdir"
	install -Dm755 ../dkimproxy_in.service "$pkgdir/usr/lib/systemd/system/dkimproxy_in.service"
	install -Dm755 ../dkimproxy_out.service "$pkgdir/usr/lib/systemd/system/dkimproxy_out.service"
}
