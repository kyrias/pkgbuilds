pkgname=python-pafy
pkgver=0.3.72
pkgrel=1

pkgdesc="Python API for YouTube"
url="http://np1.github.io/pafy"
arch=('any')
license=('GPL3')

depends=('python')
optdepends=('ffmpeg: fix issues with audio file downloads')

source=("https://github.com/np1/pafy/archive/v$pkgver.tar.gz")

sha1sums=('d4bd7de0a08676470342d6445cc70229bcc00ff2')

package() {
	cd pafy-$pkgver
	python setup.py install --root="$pkgdir" --optimize=1
}
