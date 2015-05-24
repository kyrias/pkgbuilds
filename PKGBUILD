pkgname=elementary-xfce-icons-git
pkgver=0.5.r16.g245ce2f
pkgrel=1

pkgdesc='Elementary icon-theme with improved Xfce support'
url='https://github.com/shimmerproject/elementary-xfce'
arch=('any')
license=('GPL2')

depends=('gtk-update-icon-cache')
makedepends=('git')

conflicts=('elementary-xfce-icons')

install=elementary-xfce-icons-git.install
source=('git+https://github.com/shimmerproject/elementary-xfce')

md5sums=('SKIP')

pkgver() {
	cd elementary-xfce
	git describe | sed -E 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

package() {
	mkdir -p "$pkgdir/usr/share/icons"

	cd elementary-xfce
	find ./ -type d -name "elementary-xfce*" -execdir cp -r {} "$pkgdir"/usr/share/icons/ \;

	cd "$pkgdir"/usr/share/icons
	find ./ -type f \( \
	                    -name "AUTHORS" \
	                    -o -name "CONTRIBUTORS" \
	                    -o -name "LICENSE" \
	                \) \
	    -delete
}

