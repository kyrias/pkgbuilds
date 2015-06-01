# Maintainer: Johannes Löthberg <johannes@kyriasis.com
# Contributor: Michael Hiller <glako-at-sojasau.de>

pkgname=spambayes
pkgver=1.1a6
pkgrel=4
pkgdesc="Bayesian anti-spam classifier written in Python"
arch=('any')
url="http://spambayes.sourceforge.net/"
license=('PSF')
depends=('python2' 'python2-lockfile' 'python2-setuptools')
source=("http://downloads.sourceforge.net/sourceforge/$pkgname/$pkgname-$pkgver.tar.gz")
md5sums=('d06ed6d097911ddc8db31b4e9663df4b')

package() {
	cd spambayes-$pkgver
	python2 setup.py install --root="$pkgdir"
}
