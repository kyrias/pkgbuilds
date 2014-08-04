pkgname=elementary-xfce-icons-git
pkgver=0.r941.cefa84e
pkgrel=1

pkgdesc='Elementary icon-theme with improved Xfce support'
url='https://github.com/shimmerproject/elementary-xfce'
arch=('any')
license=('GPL2')

depends=('gtk-update-icon-cache')
makedepends=('git')

conflicts=('elementary-xfce-icons')

install=elementary-xfce-icons-git.install

source=("elementary-xfce-icons::git+https://github.com/shimmerproject/elementary-xfce")
md5sums=('SKIP')

pkgver() {
	cd elementary-xfce-icons
	printf "0.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
	mkdir -p "${pkgdir}/usr/share/icons"

	cd elementary-xfce-icons
	find ./ -type d -name "elementary-xfce*" -execdir cp -r {} "${pkgdir}/usr/share/icons/" \;

	cd "${pkgdir}/usr/share/icons"
	find ./ -type f \( \
	                    -name "AUTHORS" \
	                    -o -name "CONTRIBUTORS" \
	                    -o -name "LICENSE" \
	                \) \
	    -delete
}

