pkgname=goobook-git
pkgver=1.6.r3.gb4ba7f8
pkgrel=1

pkgdesc="Search your google contacts from the command-line or mutt"
url="http://goobook.googlecode.com/"
arch=('any')
license=('GPL')

conflicts=('goobook')
provides=('goobook')

depends=('python2' 'python2-gdata>=2.0.7' 'python2-simplejson')
makedepends=('git' 'python2-setuptools')

install=goobook.install

source=('goobook::git://gitorious.org/goobook/mainline.git')
md5sums=('SKIP')


pkgver() {
	cd goobook
	git describe --tags --long | sed -E 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

package() {
	cd goobook
	sed -ie '58s/distribute/setuptools/' setup.py
	python2 setup.py install --root="$pkgdir" --optimize=1
}
