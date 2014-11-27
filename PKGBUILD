pkgname=mpv-git
pkgver=0.r39514.bebfaae
pkgrel=1

pkgdesc='Video player based on MPlayer/mplayer2 (git version)'
url='http://mpv.io'
arch=('i686' 'x86_64')
license=('GPL')

depends=('portaudio' 'ffmpeg' 'lcms2' 'libdvdread' 'libcdio-paranoia'
         'libxinerama' 'mpg123' 'libxv' 'libxkbcommon' 'libva' 'lirc-utils'
         'desktop-file-utils' 'hicolor-icon-theme' 'xdg-utils' 'lua51'
         'libxss' 'sdl2' 'smbclient' 'libguess' 'libdvdnav')
optdepends=('youtube-dl: for video-sharing website support')
makedepends=('mesa' 'python-docutils'  'git')

provides=('mpv')
conflicts=('mpv')

options=(!emptydirs)

install=mpv.install
source=('git+http://github.com/mpv-player/mpv')

md5sums=('SKIP')

pkgver() {
	cd mpv
	printf '0.r%s.%s' "$(git rev-list --count HEAD)" "$(git log -1 --pretty=format:%h)"
}

build() {
	CFLAGS="$CFLAGS -I/usr/include/samba-4.0"
	cd mpv
	./bootstrap.py
	./waf configure \
	    --prefix=/usr \
	    --confdir=/etc/mpv \
	    \
	    --disable-cocoa \
	    --disable-direct3d \
	    --disable-dsound \
	    --disable-gl-win32 \
	    --disable-wasapi \
	    \
	    --disable-libbs2b \
	    --disable-rsound \
	    --disable-sndio \
	    \
	    --enable-sdl2

	./waf build
}

package() {
	CFLAGS="$CFLAGS -I/usr/include/samba-4.0"
	cd mpv
	./waf install --destdir="$pkgdir"

	install -d "$pkgdir"/usr/share/doc/mpv/examples
	install -m644 etc/{input,example}.conf "$pkgdir"/usr/share/doc/mpv/examples
	install -m644 DOCS/{encoding.rst,tech-overview.txt} "$pkgdir"/usr/share/doc/mpv
	install -m755 TOOLS/mpv_identify.sh "$pkgdir"/usr/bin
}
