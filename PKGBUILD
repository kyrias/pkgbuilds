pkgname=gvim-hg
pkgver=7.4.488.r1.8bb4ca7fba40
pkgrel=1

pkgdesc='Vi Improved, a highly configurable, improved version of the vi text editor.'
url='http://www.vim.org/'
arch=('i686' 'x86_64')
license=('custom:vim')

groups=('editors')

depends=('gtk2' 'python3' 'ruby' 'lua' 'freetype2' 'libxt')
makedepends=('mercurial')

conflicts=('vim' 'gvim' 'vim-runtime')
provides=('vim' 'gvim' 'vim-runtime')

source=('vim'::'hg+https://vim.googlecode.com/hg/'
        'gvim.desktop'
        'remove_ro_delay.patch')

md5sums=('SKIP'
         '6e11c556ba3f2ce7dc05d9908188d604'
         '0e2d8ef1e98a58614d441b24f2242b98')

pkgver() {
	cd vim
	hg log -r "." --template "{sub('-', '.', strip(latesttag, 'v'))}.r{latesttagdistance}.{node|short}"
}

prepare(){
	cd vim
	patch -Np1 -i "$srcdir"/remove_ro_delay.patch
}

build() {
	cd vim
	./configure \
	    --enable-acl \
	    --disable-gpm \
	    --with-x=yes \
	    --prefix=/usr \
	    --enable-cscope \
	    --enable-gui=gtk2 \
	    --enable-luainterp \
	    --enable-multibyte \
	    --disable-netbeans \
	    --enable-perlinterp \
	    --enable-rubyinterp \
	    --with-features=huge \
	    --disable-pythoninterp \
	    --enable-python3interp \
	    --localstatedir=/var/lib/vim \
	    --with-compiledby='Arch Linux'
	make
}

package() {
	cd vim
	make DESTDIR="$pkgdir" install

	rm "$pkgdir"/usr/bin/ex
	rm "$pkgdir"/usr/bin/view

	# Not sure why globstar isn't enabled in makepkg
	shopt -s globstar
	rm "$pkgdir"/usr/share/man/**/ex.1*
	rm "$pkgdir"/usr/share/man/**/view.1*
	shopt -u globstar

	install -Dm644 "$srcdir"/gvim.desktop "$pkgdir"/usr/share/applications/gvim.desktop
	install -Dm644 runtime/vim48x48.png "$pkgdir"/usr/share/pixmaps/gvim.png
	install -Dm644 runtime/doc/uganda.txt "$pkgdir"/usr/share/licenses/vim/license.txt
}
