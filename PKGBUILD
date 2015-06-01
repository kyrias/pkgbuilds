# Maintainer: Johannes Löthberg <demizide@gmail.com>
# Contributor: Adrian Sampson <adrian@radbox.org>

pkgname=beets-git
pkgver=20130614
pkgrel=2
pkgdesc="Flexible music library manager and tagger - git version"
arch=('any')
url="http://beets.radbox.org/"
license=('MIT')
depends=('python2-munkres' 'mutagen'
         'python2-distribute' 'python2-unidecode'
         'python2-musicbrainzngs' 'python2-yaml') 
makedepends=('git')
optdepends=('python2-pyacoustid: acoustic fingerprinting'
            'python2-flask: web interface'
            'gstreamer0.10-python: BPD audio player plugin'
            'python2-pylast: lastgenre plugin')
provides=('beets')
conflicts=('beets')
source=('git://github.com/sampsyo/beets.git')
md5sums=('SKIP')

pkgver() {
  cd ${srcdir}/beets
  echo $(date +%Y%m%d).$(git describe --always | sed 's|-|.|g')
}

build() {
  cd ${srcdir}/beets
  python2 setup.py build
}

package() {
  cd ${srcdir}/beets
  python2 setup.py install --root=${pkgdir} --optimize=1

  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
} 
