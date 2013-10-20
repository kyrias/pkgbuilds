# Maintainer: Jan Oliver Oelerich <janoliver@oelerich.org> 
# Contributor: Johannes Löthberg <johannes@kyrias.com>

pkgname=i3pystatus-git
pkgdesc="i3status replacement written in python for the i3 window manager"
pkgver=3.1.r149.g6a3090b
pkgrel=1
arch=('i686' 'x86_64')
license=('mit')
depends=('python' 'basiciw-git' 'python-netifaces-git')
makedepends=('git' 'python-distribute')
url="https://github.com/enkore/i3pystatus.git"
source=('git+https://github.com/enkore/i3pystatus.git')
md5sums=('SKIP')

pkgver() {
  cd i3pystatus
  printf "%s" "$(git describe --always --long | sed 's/^v//;s/-/-r/' | tr - .)"
}

package() {
  cd i3pystatus
  python setup.py install --prefix=/usr --root="$pkgdir"
} 
