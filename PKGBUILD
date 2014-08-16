pkgname=dbus-user-session
pkgver=0.0.1
pkgrel=3

pkgdesc="systemd user service for dbus user bus"
url="https://theos.kyriasis.com/~kyrias"
arch=('any')
license=('custom:ISC')

depends=('systemd')

install=dbus-user-session.install
source=('dbus.socket' 'dbus.service' 'dbus.conf' 'LICENSE')

md5sums=('ae97fbcba9621d6f423193b2d67b7f52'
         'c3693a827f1d9559ecd692f19d465d01'
         '43535857bf82111dd9f8b9a0413a6e20'
         'da3b313446e8f10915bb07cd36531c49')

package() {
	install -m 644 -D dbus.socket "$pkgdir"/etc/systemd/user/dbus.socket
	install -m 644 -D dbus.service "$pkgdir"/etc/systemd/user/dbus.service

	# Dropin for the user@.service that sets the correct DBUS_SESSION_BUS_ADDRESS
	install -m 644 -D dbus.conf "$pkgdir"/etc/systemd/system/user@.service.d/dbus.conf

	install -D -m644 LICENSE "$pkgdir"/usr/share/licenses/dbus-user-session/LICENSE
}
