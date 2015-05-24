pkgname=pacman-git
pkgver=4.2.1.r160.g3d45293
pkgrel=1

pkgdesc="A library-based package manager with dependency support. git version."
url="http://www.archlinux.org/pacman/"
arch=('x86_64')
license=('GPL')

depends=('bash' 'curl' 'gpgme' 'libarchive' 'pacman-mirrorlist')
optdepends=('fakeroot: for makepkg usage as normal user')
makedepends=('git' 'asciidoc')
checkdepends=('python2' 'fakechroot')

provides=("pacman=$pkgver" 'pacman-contrib' 'libalpm.so')
conflicts=('pacman' 'pacman-contrib')

options=('strip' 'debug')

backup=(etc/pacman.conf
        etc/makepkg.conf)

source=(git://projects.archlinux.org/pacman.git
        pacman.conf
        makepkg.conf)

sha1sums=('SKIP'
          '3c1bddf27602e02fb57801c0ea7313b3869acc92'
          'f2ef3115adaf2aa5c13a1ab7e948c21028451465')

pkgver() {
	cd pacman
	git describe --long | sed -r 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
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
	make DESTDIR="$pkgdir" -C contrib install

	# install Arch specific stuff
	install -dm755 "$pkgdir"/etc
	install -m644 "$srcdir"/pacman.conf "$pkgdir"/etc/
	install -m644 "$srcdir"/makepkg.conf "$pkgdir"/etc/

	# set things correctly in the default conf file
	sed -i "$pkgdir/etc/makepkg.conf" \
		-e "s|@CARCH[@]|x86_64|g" \
		-e "s|@CHOST[@]|x86_64-unknown-linux-gn|g" \
		-e "s|@CARCHFLAGS[@]|-march=x86-64 |g"


	install -Dm644 contrib/PKGBUILD.vim "$pkgdir"/usr/share/vim/vimfiles/syntax/PKGBUILD.vim
	install -dm755 "$pkgdir"/usr/share/vim/vimfiles/ftdetect
	echo "au BufNewFile,BufRead PKGBUILD set filetype=PKGBUILD" \
		>"$pkgdir"/usr/share/vim/vimfiles/ftdetect/PKGBUILD.vim

	# install completion files
	rm -r "$pkgdir"/etc/bash_completion.d
	install -Dm644 contrib/bash_completion "$pkgdir"/usr/share/bash-completion/completions/pacman
	install -Dm644 contrib/zsh_completion "$pkgdir"/usr/share/zsh/site-functions/_pacman

	for f in makepkg pacman-key; do
		ln -s pacman "$pkgdir"/usr/share/bash-completion/completions/"$f"
	done

	install -Dm644 contrib/PKGBUILD.vim "$pkgdir"/usr/share/vim/vimfiles/syntax/PKGBUILD.vim
}
