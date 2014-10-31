pkgname=pacman-git
pkgver=4.1.2.r460.ga0cfed7
pkgrel=1

pkgdesc="A library-based package manager with dependency support. git version."
url="http://www.archlinux.org/pacman/"
arch=('i686' 'x86_64')
license=('GPL')

depends=('bash' 'curl' 'gpgme' 'libarchive' 'pacman-mirrorlist')
makedepends=('git' 'asciidoc')
optdepends=('fakeroot: for makepkg usage as normal user')
checkdepends=('python2' 'fakechroot')

provides=("pacman=$pkgver" 'pacman-contrib' 'libalpm.so')
conflicts=('pacman' 'pacman-contrib')

options=('!libtool' '!strip')

backup=(etc/pacman.conf
        etc/makepkg.conf)

source=(git://projects.archlinux.org/pacman.git)

sha1sums=('SKIP')

pkgver() {
	cd pacman
	git describe | sed -r 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
	cd pacman

	./autogen.sh
	./configure \
	    --prefix=/usr \
	    --sysconfdir=/etc \
	    --localstatedir=/var \
	    --enable-doc \
	    --enable-git-version \
	    --enable-debug \
	    --with-scriptlet-shell=/usr/bin/bash \
	    --with-ldconfig=/usr/bin/ldconfig

	make
	make -C contrib
}

check() {
	make -C "pacman" check
}

package() {
	cd pacman

	make DESTDIR="$pkgdir" install

	# set things correctly in the default conf file
	sed -i "$pkgdir/etc/makepkg.conf" \
		-e "s|@CARCH[@]|$CARCH|g" \
		-e "s|@CHOST[@]|x86_64-unknown-linux-gn|g" \
		-e "s|@CARCHFLAGS[@]|-march=x86-64 |g"

	# contrib
	make DESTDIR="$pkgdir" -C contrib install

	install -Dm644 contrib/PKGBUILD.vim "$pkgdir"/usr/share/vim/vimfiles/syntax/PKGBUILD.vim
	install -dm755 "$pkgdir"/usr/share/vim/vimfiles/ftdetect
	echo "au BufNewFile,BufRead PKGBUILD set filetype=PKGBUILD" \
		>"$pkgdir"/usr/share/vim/vimfiles/ftdetect/PKGBUILD.vim

	# install completion files
	rm -r "$pkgdir"/etc/bash_completion.d
	install -Dm644 contrib/bash_completion "$pkgdir"/usr/share/bash-completion/completions/pacman
	for f in makepkg pacman-key; do
		ln -s pacman "$pkgdir"/usr/share/bash-completion/completions/"$f"
	done

	install -Dm644 contrib/zsh_completion "$pkgdir"/usr/share/zsh/site-functions/_pacman
}
