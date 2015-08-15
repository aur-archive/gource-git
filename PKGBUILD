# Contributor: matthiaskrgr <matthiaskrgr _strange_curverd_character_ freedroid D0T org>

pkgname=gource-git
pkgver=0.43
pkgver(){
    cd gource
    git describe --tags | sed -e 's/^gource\-//' -e 's/-/./g'
}
pkgrel=1
pkgdesc="software version control visualization"
license=('GPL3')
arch=('i686' 'x86_64')
url="http://code.google.com/p/gource/"
makedepends=('git' 'autoconf' 'boost' 'glm' 'mesa-libgl')
depends=('sdl2_image' 'pcre' 'glew' 'boost-libs' 'freetype2' 'tinyxml' 'libgl')
optdepends=('ffmpeg: to convert the ppm stream (gource -o) to a video')
conflicts=('gource')
provides=('gource')
changelog=changelog
source=('gource::git://github.com/acaudwell/Gource.git'
		'changelog')
sha1sums=('SKIP'
          'eeb35c7490672b16b2d8faf45e2a7a7abb37c4c6')


prepare() {
	msg "Preparing build..."
	cd "$srcdir"/"gource"
	git submodule init
	git submodule update
	}

build() {
	msg "Starting compilation..."
	cd "$srcdir"/"gource"

	msg "Running autogen.sh..."
	./autogen.sh
	msg "Running configure..."
	./configure --prefix=/usr --with-tinyxml
	msg "Running make..."
	make
}

package() {
	cd "$srcdir"/"gource"
	make DESTDIR=$pkgdir install
	msg "Compiling done."
}
