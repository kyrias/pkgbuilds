pkgname=bemenu-git
pkgver=r216.064e937
pkgrel=1

pkgdesc='Dynamic menu library and client program inspired by dmenu'
url='https://github.com/Cloudef/bemenu'
license=('GPL3' 'LGPL3')
arch=('i686' 'x86_64')

depends=('pango')
makedepends=('git' 'cmake' 'libxkbcommon' 'libxinerama' 'wayland')
optdepends=('wayland: For the wayland backend.'
            'libxkbcommon: For the wayland backend.'
            'libxinerama: For the x11 backend.'
            'ncurses: For the curses backend.')

provides=('bemenu')
conflicts=('bemenu')

source=('git+https://github.com/Cloudef/bemenu')

md5sums=('SKIP')

pkgver() {
    cd bemenu
    printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git describe --always)"
}

build() {
    cd bemenu
    cmake -DCMAKE_INSTALL_PREFIX=/usr
    make
}

check() {
    cd bemenu
    make test
}

package() {
    cd bemenu
    make DESTDIR="$pkgdir" install
}
