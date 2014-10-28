pkgname=weechat-git
pkgver=1.0.r77.gf91f57f
pkgrel=1

pkgdesc="Fast, light & extensible IRC client (curses UI)"
url="http://www.weechat.org/"
arch=('i686' 'x86_64')
license=('GPL3')

depends=('gnutls' 'ncurses-git' 'libgcrypt')
optdepends=('perl' 'python' 'lua' 'tcl' 'ruby' 'aspell')
makedepends=('git' 'cmake' 'pkgconfig' 'perl' 'python2' 'lua' 'tcl' 'ruby' 'aspell')

provides=('weechat')
conflicts=('weechat')

options=(!makeflags)

source=("git+https://github.com/weechat/weechat.git")

md5sums=('SKIP')

pkgver(){
	cd weechat
	git describe --long | sed -E 's/^v//;s/-rc/rc/;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
	cd weechat
	cmake -DPREFIX=/usr \
	      -DENABLE_PYTHON3=ON \
	      -DPYTHON_EXECUTABLE=/usr/bin/python \
	      -DPYTHON_LIBRARY=/usr/lib/libpython3.so\
	      -DENABLE_MAN=ON \
	      -DENABLE_DOC=OFF \
	      -DWEECHAT_HOME=~/.config/weechat
	make
}

package() {
	make -C weechat DESTDIR="$pkgdir" install
}
