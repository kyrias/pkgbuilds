# Maintainer: Adrian Sampson <adrian@radbox.org>
# Contributor: Johannes Löthberg <johannes@kyriasis.com>

pkgname=beets-git
pkgver=1.3.1.r35.gc82cd29
pkgrel=1
pkgdesc="Flexible music library manager and tagger - git version"
arch=('any')
url="http://beets.radbox.org/"
license=('MIT')
depends=('python2-munkres' 'mutagen'
		 'python2-setuptools' 'python2-unidecode'
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
	cd beets
	printf "%s" "$(git describe --tags --long | sed 's/^v//;s/-/-r/' | tr - .)" 
}

build() {
	cd beets
	python2 setup.py build
}

package() {
	cd beets
	python2 setup.py install --root="$pkgdir" --optimize=1

	install -D -m644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
} 

# vim: set ts=4 sw=4 noet:
