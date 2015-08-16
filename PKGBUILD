# Maintainer: Rikard Falkeborn <rikard.falkeborn@gmail.com>
# Constributor: Wilfried Fauvel <wilfried.fauvel at gmail>
# Contributor: orbisvicis <orbisvicis at gmail dot com>
# Contributor: Martti K?hne <mysatyre at gmail dot com>

pkgname=mandelbulber-svn
_pkg=mandelbulber
pkgver=436  
pkgrel=1
pkgdesc="An experimental application designed to render 3D fractals such as the Mandelbulb, Mandelbox, BulbBox, JuliaBulb, Menger Sponge, and Iterated Function Systems"
arch=("i686" "x86_64")
url="http://sites.google.com/site/mandelbulber/"
license=("GPL3")
depends=('gtk2' 'libjpeg-turbo' 'desktop-file-utils')
makedepends=('subversion' 'imagemagick')
provides=("$_pkg")
conflicts=("$_pkg")
install="${pkgname}.install"
source=("${_pkg}::svn+http://mandelbulber.googlecode.com/svn/trunk/")
md5sums=('SKIP')


pkgver() {
  cd "$srcdir/${_pkg}"
  svnversion | tr -d [A-z]
}

build() {
  cd "$srcdir/${_pkg}/makefiles"
  make all
}

package() {
  install -m755 -d "${pkgdir}/usr/bin"
  install -Dm755 "${srcdir}/${_pkg}/makefiles/${_pkg}" \
                 "${pkgdir}/usr/bin/"
  install -m755 -d "${pkgdir}/usr/share/${_pkg}"
  cp -r "${srcdir}/${_pkg}/share/"* "${pkgdir}/usr/share/${_pkg}"
  install -D -m644 "$srcdir/${_pkg}/${_pkg}.desktop" "${pkgdir}/usr/share/applications/${_pkg}.desktop"
  #install -D -m644 "$srcdir/${_pkg}/${_pkg}-opencl.desktop" "${pkgdir}/usr/share/applications/${_pkg}-opencl.desktop" # Currently just an empty file
  convert "$srcdir/${_pkg}/${_pkg}.ico" "$srcdir/${_pkg}/${_pkg}.png"
  install -D -m644 "$srcdir/${_pkg}/${_pkg}.png" "$pkgdir/usr/share/$_pkg"
}
