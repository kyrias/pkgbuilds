pkgname=sv_dvorak
pkgver=1
pkgrel=3

pkgdesc="A Swedish dvorak keyboard layout (Xorg driver)"
url="http://tlundqvist.org/sv_dvorak/"
arch=(any)
license=('GPL')

depends=('xorg-server')

install=sv_dvorak.install

source=("http://tlundqvist.org/sv_dvorak/drivers/se_sv_dvorak_new.xorg")
md5sums=('1e4a2818c89e60001a1ec2d98911a0a0')

package() {
	install -Dm644 se_sv_dvorak_new.xorg "$pkgdir"/usr/share/X11/xkb/symbols/se_sv_dvorak
}
