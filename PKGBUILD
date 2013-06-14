# Maintainer: Johannes Löthberg <demizide@gmail.com>
# Contributor: Adrian Sampson <adrian@radbox.org>

pkgname=beets-git
pkgver=20130614
pkgrel=1
pkgdesc="Flexible music library manager and tagger - git version"
arch=('any')
url="http://beets.radbox.org/"
license=('MIT')
makedepends=('git')
depends=('python2-munkres' 'mutagen'
         'python2-distribute' 'python2-unidecode'
         'python2-musicbrainzngs' 'python2-yaml') 
optdepends=('python2-pyacoustid: acoustic fingerprinting'
            'python2-flask: web interface'
            'gstreamer0.10-python: BPD audio player plugin'
            'python2-pylast: lastgenre plugin')
provides=('beets')
conflicts=('beets')
source=('git://github.com/sampsyo/beets.git')
md5sums=('SKIP')

build() {
  cd ${srcdir}/beets
  python2 setup.py build
}

package() {
  cd ${srcdir}/beets
  python2 setup.py install --root=${pkgdir}
} 

pkgver() {
  cd ${srcdir}/beets
  echo $(date +%Y%m%d).$(git describe --always | sed 's|-|.|g')
}
