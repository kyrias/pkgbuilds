pkgname=thinkfan
pkgver=0.9.1
pkgrel=1

pkgdesc="A minimalist fan control program. Supports the sysfs hwmon interface and thinkpad_acpi"
url='http://thinkfan.sourceforge.net/'
arch=('i686' 'x86_64')
license=('GPL')

install=thinkfan.install
source=("http://downloads.sourceforge.net/project/$pkgname/$pkgname-$pkgver.tar.gz"
        'thinkfan.install' 'thinkfan.service' 'thinkpad_acpi.conf')

md5sums=('a981142f2c52ee4b0af69d5abbe03ced'
         '4d532f96317d54c48d9cd1139eac747f'
         '0197bde7c3d3b64d34635ead78cf3437'
         'bca920d066846e5811a2465aefa13012')

build() {
	cd $pkgname-$pkgver
	cmake . -DUSE_ATASMART:BOOL=ON
	sed -i "s|/usr|$pkgdir/usr|" cmake_install.cmake
	cmake --build .
}

package() {
	cd $pkgname-$pkgver
	make install
	install -D -m644 $srcdir/thinkpad_acpi.conf $pkgdir/etc/modprobe.d/thinkpad_acpi.conf
	install -D -m644 $srcdir/$pkgname.service $pkgdir/usr/lib/systemd/system/$pkgname.service
}
