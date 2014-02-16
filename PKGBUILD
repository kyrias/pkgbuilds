# Maintainer: Raphael Scholer <rscholer@gmx.de>

pkgname=elementary-xfce-icons-git
pkgver=0.3_73_g082b3d4
pkgrel=1
pkgdesc='Elementary icon-theme with improved Xfce support'
arch=('any')
url='https://github.com/shimmerproject/elementary-xfce'
license=('GPL2')
makedepends=('git')
depends=('gtk-update-icon-cache')
conflicts=('elementary-xfce-icons')
install=elementary-xfce-icons-git.install
source=("$pkgname::git+https://github.com/shimmerproject/elementary-xfce")
md5sums=('SKIP')

pkgver() {
	cd $pkgname
	echo "$(git describe --always |sed 's#-#_#g;s#v##')"
}

package() {
	mkdir -p "${pkgdir}/usr/share/icons"

	cd $pkgname
	find ./ -type d -name "elementary-xfce*" -execdir cp -r {} "${pkgdir}/usr/share/icons/" \;

	cd "${pkgdir}/usr/share/icons"
	find ./ -type f \( \
						-name "AUTHORS" \
						-o -name "CONTRIBUTORS" \
						-o -name "LICENSE" \
					\) \
		-delete
}

