pkgname=vte3-select-text-git
pkgver=0.38.1.r1.gbc68e69
pkgrel=1

pkgdesc="Virtual Terminal Emulator widget for use with GTK3"
url="http://www.gnome.org"
arch=('i686' 'x86_64')
license=('LGPL')

options=('!libtool' '!emptydirs')

depends=('gtk3' 'vte-common')
makedepends=('intltool' 'gobject-introspection' 'gtk3' 'python2' 'vala' 'git')

provides=('vte3')
conflicts=('vte3' 'vte3-select-text')

source=('expose_select_text.patch'
        'git://git.gnome.org/vte#branch=vte-0-38')

sha256sums=('f9c28813843314210b53037373c657c6b2389e3e5b5607226b7acaa3a7964a7f'
            'SKIP')

pkgver() {
	cd vte
	git describe | sed 's/-/.r/; s/-/./'
}

prepare() {
	cd vte
	patch -p1 -i "$srcdir"/expose_select_text.patch
}

build() {
	cd vte

	./autogen.sh
	./configure \
	    --prefix=/usr \
	    --sysconfdir=/etc \
	    --libexecdir=/usr/lib/vte \
	    --localstatedir=/var \
	    --disable-static \
	    --enable-introspection

	make
}

package() {
	cd vte
	make DESTDIR="$pkgdir" install
	rm "$pkgdir"/etc/profile.d/vte.sh
}
