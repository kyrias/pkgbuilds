pkgname=ncurses-git
pkgver=5.9.r199.g8d00601
pkgrel=1

pkgdesc='Unofficial git mirror of snapshots from ftp://invisible-island.net/ncurses/current/'
url='http://ncurses.scripts.mit.edu/?p=ncurses.git'
arch=('i686' 'x86_64')
license=('MIT')

makedepends=('git')

provides=('ncurses' 'libncursesw.so')
conflicts=('ncurses' 'libncursesw.so')

source=('git://ncurses.scripts.mit.edu/ncurses.git')

md5sums=('SKIP')

pkgver() {
	cd ncurses
	git describe --tags | sed 's/^v//; s/-/.r/; s/-/./'
}

build() {
	mkdir ncurses{,w}-build

	cd ncursesw-build
	# add --enable-ext-colors and --enable-ext-mouse with next soname bump
	../ncurses/configure \
	    --prefix=/usr \
	    --with-shared \
	    --with-normal \
	    --without-ada  \
	    --enable-widec \
	    --without-debug \
	    --enable-pc-files
	make

	# libraries for external binary support
	cd "$srcdir"/ncurses-build
	[[ $CARCH = "x86_64" ]] && CONFIGFLAG="--with-chtype=long"
	../ncurses/configure --prefix=/usr \
	    --with-shared \
	    --with-normal \
	    --without-ada \
	    --without-debug \
	    $CONFIGFLAG
	make
}

package() {
	cd ncursesw-build
	make DESTDIR="$pkgdir" install

	# fool packages looking to link to non-wide-character ncurses libraries
	for lib in ncurses form panel menu; do
		printf 'INPUT(-l%sw)\n' "$lib" > "$pkgdir"/usr/lib/lib"$lib".so
	done

	for lib in ncurses ncurses++ form panel menu; do
		ln -s "$lib"w.pc "$pkgdir"/usr/share/pkgconfig/"$lib".pc
	done

	# some packages look for -lcurses during build
	printf 'INPUT(-lncursesw)\n' > "$pkgdir"/usr/lib/libcursesw.so
	ln -s libncurses.so "$pkgdir"/usr/lib/libcurses.so

	# non-widec compatibility libraries
	cd "$srcdir"/ncurses-build
	for lib in ncurses form panel menu; do
		install -Dm755 lib/lib"$lib".so.5.9 "$pkgdir"/usr/lib/lib"$lib".so.5.9
		ln -s lib"$lib".so.5.9 "$pkgdir"/usr/lib/lib"$lib".so.5
	done

	install -Dm755 "$srcdir"/ncurses/COPYING "$pkgdir"/usr/share/licenses/ncurses/COPYING
}
