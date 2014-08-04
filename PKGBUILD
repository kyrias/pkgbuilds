pkgname=kittypack-git
pkgver=0.r15.cb4edf4
pkgrel=1

pkgdesc="A silly little tool to get info from archlinux.org/packages"
url="https://github.com/MrElendig/kittypack"
arch=('any')
license=('AGPL3')

backup=('etc/kittypack.conf')

depends=('python' 'python-requests' 'python-docopt' 'python-yaml')
makedepends=('git')

source=(git://github.com/MrElendig/kittypack.git)
sha1sums=('SKIP')

pkgver() {
	cd kittypack
	printf "0.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
	cd kittypack
	python3 setup.py install --root="$pkgdir"
}
