pkgname=weechat-git
pkgver=1.2.r10.g3262599
pkgrel=1

pkgdesc="Fast, light & extensible IRC client (curses UI)"
url="http://www.weechat.org/"
arch=('i686' 'x86_64')
license=('GPL3')

depends=('gnutls' 'ncurses-git' 'libgcrypt')
optdepends=('perl' 'python2' 'lua' 'tcl' 'ruby' 'aspell')
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

	# https://github.com/weechat/weechat/issues/287
	export CFLAGS="$CFLAGS -fPIC"

	cmake -DCMAKE_INSTALL_PREFIX=/usr \
	      -DPYTHON_EXECUTABLE=/usr/bin/python2 \
	      -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so\
	      -DENABLE_MAN=ON \
	      -DENABLE_DOC=OFF \
	      -DWEECHAT_HOME=~/.config/weechat
	make
}

package() {
	make -C weechat DESTDIR="$pkgdir" install
}
