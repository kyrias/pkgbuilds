pkgname=i3pystatus-git
pkgver=3.30.r19.g1dbbc01
pkgrel=1

pkgdesc="i3status replacement written in python for the i3 window manager"
url="https://github.com/enkore/i3pystatus.git"
arch=('i686' 'x86_64')
license=('MIT')

depends=('python' 'basiciw-git' 'python-netifaces-git')
makedepends=('git' 'python-distribute')

source=('git+https://github.com/enkore/i3pystatus.git')

md5sums=('SKIP')

pkgver() {
	cd i3pystatus
	git describe --always --long | sed 's/^v//; s/-/-r/; s/-/./g'
}

package() {
	cd i3pystatus
	python setup.py install --prefix=/usr --root="$pkgdir"
}
