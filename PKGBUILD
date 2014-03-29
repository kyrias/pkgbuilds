# Maintainer: Johannes Löthberg <johannes@kyriasis.com>
# Contributor: neersighted <n@neersighted.com>
# Contributor: boyska <piuttosto@logorroici.org>

pkgname=mutt-kz-git
pkgver=git
pkgrel=1

pkgdesc='Small but powerful text-based mail client'
arch=('i686' 'x86_64')
url='https://github.com/karelzak/mutt-kz'
license=('GPL')

source=('git+https://github.com/karelzak/mutt-kz.git' 'xdg.patch'
        'trash.patch::https://www.cs.oberlin.edu/~kuperman/help/code/patch-1.5.20.bk.trash_folder-purge_message.1.txt')
sha1sums=('SKIP'
          '8cbae5a7ade3812cbdcb8a8dfabb29b042b7296a'
          'b63fe4e7ea2a113819558862be1387364ec24213')

depends=('gdbm' 'gpgme' 'openssl>=0.9.8e' 'libsasl' 'mime-types' 'ncurses' 'notmuch' 'zlib')
makedepends=('git' 'gnupg' 'libxslt')

conflicts=('mutt')
provides=('mutt')

pkgver() {
  cd mutt-kz
  git describe --always | sed 's/^v//;s/-/./g'
}

prepare() {
  cd mutt-kz

  # Apply patches.
  patch -p1 < "$srcdir/trash.patch"
  patch -p1 < "$srcdir/xdg.patch"
}

build() {
  cd mutt-kz

  # Configure the build.
 ./prepare \
    --prefix=/usr \
    --sysconfdir=/etc \
    --enable-debug \
    --enable-gpgme \
    --enable-hcache \
    --enable-imap \
    --enable-notmuch \
    --enable-pgp \
    --enable-pop \
    --enable-smtp \
    --with-idn \
    --with-sasl \
    --with-ssl=/usr

  # Build it!
  make
}

package() {
  cd mutt-kz

  # Install the program.
  make DESTDIR="$pkgdir" install

  # Provided by the mime-types package.
  rm "$pkgdir/etc/mime.types"
}
