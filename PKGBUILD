# Maintainer: Johannes Löthberg <kyrias@archlinux.info>
# Contributor: Gaetan Bisson <bisson@archlinux.org>

pkgname=quassel-light
pkgver=0.8.0
pkgrel=4
pkgdesc="Modern, cross-platform, distributed IRC client; built with few dependencies"
arch=('i686' 'x86_64')
url="http://quassel-irc.org/"
license=('GPL')
depends=('qt4')
optdepends=('qca-ossl')
makedepends=('cmake' 'automoc4')
provides=('quassel' 'quasselcore' 'quasselclient')
conflicts=('quassel' 'quasselcore' 'quasselclient')
install=quassel.install
backup=(etc/conf.d/quassel)
source=("http://quassel-irc.org/pub/quassel-$pkgver.tar.bz2"
        'quassel.service'
        'quassel.conf')
sha256sums=('a3515bd18e2b100eb9a72480e76b1faefaa5e84cdb236b6af1f05b477a1e9071'
            '91a1aaae47d41c11aa418dd560039ddbbfb659e02b86379d8c4789c5ada362d3'
            'f3031ea8217e01ba42cea14606169e3e27affa5918968ffd5a03c21ae92fe2b8')


build() {
  [[ ! -d build ]] && mkdir build
  cd build

  cmake \
    -DCMAKE_INSTALL_PREFIX=/usr/ \
    -DWITH_KDE=OFF \
    -DWITH_WEBKIT=OFF \
    -DWITH_PHONON=OFF \
    -DWITH_LIBINDICATE=OFF \
    -DCMAKE_BUILD_TYPE="Release" \
    ../quassel-${pkgver}/ \
    -Wno-dev \

  make
}

package() {
  cd build

  make DESTDIR="${pkgdir}" install

  install -Dm644 "${srcdir}"/quassel.service \
    "${pkgdir}"/usr/lib/systemd/system/quassel.service
  install -Dm644 "${srcdir}"/quassel.conf \
    "${pkgdir}"/etc/conf.d/quassel
}
