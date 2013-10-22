# Maintainer: Daniel Wallace <danielwallace at gtmanfred dot com>
# Contributor: Dmitry Korzhevin <dkorzhevin AT gmail DOT com>
# Contributor: Mark Foxwell <fastfret79@archlinux.org.uk>
# Contributor: Licia Todd <tigrmesh at aol dot com>
# Contributor: Tim Zebulla <amon at faumrahrer dot de>
# Contributor: Johannes Löthberg <johannes@kyriasis.com>

pkgname=weechat-git
pkgver=0.4.2.r24.g3088d31
pkgrel=2
pkgdesc="Fast, light & extensible IRC client (curses UI)"
arch=('i686' 'x86_64')
url="http://www.weechat.org/"
license=('GPL3')
depends=('gnutls' 'ncurses' 'libgcrypt')
makedepends=('git' 'cmake' 'pkgconfig' 'perl' 'python2' 'lua' 'tcl' 'ruby' 'aspell')
optdepends=('perl' 'python2' 'lua' 'tcl' 'ruby' 'aspell')
provides=('weechat')
conflicts=('weechat')
options=(!libtool)
source=("git://git.savannah.nongnu.org/weechat.git")
md5sums=('SKIP')

pkgver(){
	cd weechat
	printf "%s" "$(git describe --tags --long | sed 's/^v//; s/-/-r/' | tr - .)" 
}

build() {
	cd weechat
	cmake -DPREFIX=/usr \
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

# vim: set ts=4 sw=4 noet:
