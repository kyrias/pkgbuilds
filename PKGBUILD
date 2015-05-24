pkgname=kittypack-git
pkgver=0.r20.b4b22b9
pkgrel=1

pkgdesc="A silly little tool to get info from archlinux.org/packages"
url="https://github.com/MrElendig/kittypack"
arch=('any')
license=('AGPL3')

depends=('python' 'python-requests' 'python-docopt' 'python-yaml')
makedepends=('git')

backup=('etc/kittypack.conf')

source=(git://github.com/MrElendig/kittypack.git)

sha256sums=('SKIP')

pkgver() {
	cd kittypack
	printf "0.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
	cd kittypack
	python3 setup.py install --root="$pkgdir"
}
