# $Id: PKGBUILD 58551 2009-11-08 22:37:12Z eric $
# Contributor:	dorphell			<archlinux.org: dorphell>
# Contributor:	Travis Willard			<archlinux.org: travis>
# Contributor:	Douglas Soares de Andrade	<archlinux.org: douglas>
# Contributor:	Jesse Jaara			<gmail.com, mail.ru: jesse.jaara> (original maintainer) 
# Maintainer:   Matej Lach                      <matej.lach@gmail.com>
# Please remove '-working' from 'pkgname' before use!

pkgname=libpng12-working
_realname=libpng
pkgver=1.2.46
pkgrel=1
pkgdesc="A collection of routines used to create PNG format graphics files"
arch=('i686' 'x86_64')
url="http://www.libpng.org/pub/png/libpng.html"
license=('custom')
depends=('zlib')
options=('!libtool')
source=("http://sourceforge.net/projects/libpng/files/libpng12/${pkgver}/libpng-${pkgver}.tar.xz"
        "http://sourceforge.net/projects/apng/files/libpng/libpng12/libpng-${pkgver}-apng.patch.gz")

build() {
  cd "${srcdir}/${_realname}-${pkgver}"

  patch -Np0 -i "${srcdir}/libpng-${pkgver}-apng.patch"

  libtoolize --force --copy
  aclocal
  autoconf
  automake --add-missing

  ./configure --prefix=/usr

  make ECHO=echo
}

package() {
  cd "${srcdir}/${_realname}-${pkgver}"

  make ECHO=echo DESTDIR="${pkgdir}" install

  rm -rf "${pkgdir}/usr/share"
  rm -rf "${pkgdir}/usr/bin/libpng-config"
  rm -rf "${pkgdir}/usr/lib/"{libpng.so,libpng.a}
  rm -fr "${pkgdir}/usr/lib/pkgconfig/libpng.pc"
  rm -rf "${pkgdir}/usr/include/"{pngconf.h,png.h}
}
md5sums=('4a0a9662710dab35760ab8ecd6835e65'
         '13b019dac361f88faed8989f0c6d5f04')
