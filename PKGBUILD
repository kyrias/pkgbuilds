pkgname=vte3-select-text-git
pkgver=0.36.2.r13.g2991e7a
pkgrel=1

pkgdesc="Virtual Terminal Emulator widget for use with GTK3"
url="http://www.gnome.org"
arch=('i686' 'x86_64')
license=('LGPL')

options=('!libtool' '!emptydirs')

depends=('gtk3' 'vte-common')
makedepends=('intltool' 'gobject-introspection' 'gtk3' 'gtk-doc' 'gperf' 'git')

provides=('vte3')
conflicts=('vte3' 'vte3-select-text')

source=('expose_select_text.patch'
        'git://git.gnome.org/vte#branch=vte-0-36')
sha256sums=('37fc0ecd4939c3b14f36dace31b54507e0f1cf1fc95a07ae079b1997d0481d7e'
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
	    --enable-introspection \
	    --libexecdir=/usr/lib/vte \
	    --localstatedir=/var --disable-static
	make
}

package() {
	cd vte

	make DESTDIR="$pkgdir" install
	rm "$pkgdir"/usr/lib/vte/gnome-pty-helper
}
