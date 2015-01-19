pkgname=earnestly-font-collection-git
pkgver=0.r16.9ef8993
pkgrel=1

pkgdesc="Collection of Earnestly’s fonts"
arch=('any')
url="https://github.com/Earnestly/fonts"
license=('custom')

provides=('font-fncp6' 'font-fncp7')
conflicts=('font-fncp6' 'font-fncp7')

depends=('fontconfig')
makedepends=('fontforge')

install=fonts.install

source=('git+https://github.com/Earnestly/fonts.git')

sha256sums=('SKIP')

pkgver() {
	cd fonts
	printf "0.r%s.%s" "$(git rev-list --count HEAD)" "$(git describe --always)"
}

build() {
	for font in fncp6 fncp7; do
		cd "$srcdir"/fonts/"$font"
		make
	done
}

package() {
	for font in fncp6 fncp7; do
		cd "$srcdir"/fonts/"$font"
		install -d "$pkgdir"/usr/share/fonts/"$font"
		install -m644 *.otf -t "$pkgdir"/usr/share/fonts/"$font"
	done
}
