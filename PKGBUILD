pkgname=mps-youtube
pkgver=0.2.4
pkgrel=1

pkgdesc="Terminal based YouTube jukebox with playlist management"
url='https://github.com/np1/mps-youtube'
arch=('any')
license=('GPL3')

depends=('python' 'python-setuptools' 'python-pafy')
optdepends=('mpv: Alternative to mplayer for playback'
            'mplayer: Alternative to mpv for playback'
            'ffmpeg: for transcoding downloaded content'
            'xclip: for copying content to the clipboard')

install=mps-youtube.install
source=("https://github.com/np1/mps-youtube/archive/v$pkgver.tar.gz")

sha256sums=('3ebd1128dcd67754eebfd36f25e36f4dc7bfc9593f08cb30a8cb0b4e4a99f652')

package() {
	cd mps-youtube-$pkgver
	python setup.py install --root="$pkgdir" --optimize=1
}
