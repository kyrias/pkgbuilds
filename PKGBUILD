# Maintainer: Johannes Löthberg <johannes@kyriasis.com>
# Contributor: Vinícius dos Santos Oliveira <vini.ipsmaker@gmail.com>
# Contributor: Emmanuel Gil Peyrot <linkmauve@linkmauve.fr>

pkgname=openhexagon
pkgver=2.0RC1
pkgrel=1
pkgdesc="C++ open source clone of Super Hexagon. (binary)"
arch=('i686' 'x86_64')
url="http://vittorioromeo.info/projects.html"
options=(!strip)
license=('custom:AFL')
depends=('lua51' 'gcc-libs-multilib' 'mesa' 'libjpeg-turbo' 'sfml')
source=(OpenHexagon.tar::'http://vittorioromeo.info/Misc/Temp/OpenHexagon2.0-RC1.xz'
		'https://raw.github.com/SuperV1234/SSVOpenHexagon/master/LICENSE' OpenHexagon)
md5sums=('758df0cb21c5a565f4039c5e0bc6b2c6'
		 '2002c3e1decad54ffe535efef6723a5c'
		 'cedfdc5a1bfdf70f730f06466a8d28c5')

prepare() {
	cd testInstall2
	(cd x86
	find -not -type d -not -name "SSVOpenHexagon" -not -name "libsfml*" -exec rm {} +)
	find -exec chmod 755 {} +
	sed -i 's|\./x86|/opt/openhexagon2.0-RC1/x86|g' OpenHexagon
	mv ../OpenHexagon .
}
package() {
	install -d "$pkgdir"/opt/openhexagon2.0-RC1
	cp -r testInstall2/* "$pkgdir"/opt/openhexagon2.0-RC1

	install -d "$pkgdir"/usr/bin
	ln -s /opt/openhexagon2.0-RC1/OpenHexagon "$pkgdir"/usr/bin/openhexagon

	# Need world writeable Profiles for creating profiles and config for... config
	chmod 777 "$pkgdir"/opt/openhexagon2.0-RC1/{Profiles,config.json}

	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
