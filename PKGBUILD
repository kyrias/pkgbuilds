# Maintainer: nblock <nblock [/at\] archlinux DOT us>
# Contributor: Frederik Alkærsig (FALKER) <havnelisten AT gmail.com>

pkgname=thinkfan
pkgver=0.8.1
pkgrel=7
pkgdesc="A minimalist fan control program. Supports the sysfs hwmon interface and thinkpad_acpi"
arch=('i686' 'x86_64')
license=('GPL')
source=("http://downloads.sourceforge.net/project/$pkgname/$pkgname-$pkgver.tar.gz"
		'thinkfan.install' 'thinkfan.service' 'thinkpad_acpi.conf')
url='http://thinkfan.sourceforge.net/'
install=thinkfan.install
md5sums=('aaa6c88bab3b43756ac5a1638622828c'
		 '76553f63dc55a6e09a429bb4e28eb649'
		 '0197bde7c3d3b64d34635ead78cf3437'
		 'bca920d066846e5811a2465aefa13012')

build() {
	cd $pkgname-$pkgver
	make
}

package() {
	cd $pkgname-$pkgver
	install -D -m755 $pkgname $pkgdir/usr/bin/$pkgname
	install -D -m644 $srcdir/thinkpad_acpi.conf $pkgdir/etc/modprobe.d/thinkpad_acpi.conf
	install -D -m644 README $pkgdir/usr/share/doc/$pkgname/README
	install -D -m644 $srcdir/$pkgname.service $pkgdir/usr/lib/systemd/system/$pkgname.service
	cp -r examples $pkgdir/usr/share/doc/$pkgname/
}
