pkgname=archtk-timer
pkgver=0
pkgrel=1

pkgdesc="Useless timer"
url="https://github.com/EliteTK/c-stuff"
arch=('i686' 'x86_64')
license=('GPL')

source=("git+https://github.com/EliteTK/c-stuff.git")

md5sums=('SKIP')

pkgver() {
	cd c-stuff
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	make -C c-stuff timer
}

package() {
	install -Dm755 c-stuff/timer "$pkgdir"/usr/bin/timer
}
