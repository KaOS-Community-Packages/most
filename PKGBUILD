pkgname=most
pkgver=5.1.0
pkgrel=1
pkgdesc="A terminal pager similar to 'more' and 'less'"
arch=('x86_64')
depends=('slang')
license=('GPL')
url="http://www.jedsoft.org/most/index.html"
install="${pkgname}.install"
source=(https://www.jedsoft.org/releases/${pkgname}/${pkgname}-${pkgver}.tar.gz)
sha1sums=('db811669a6b22c15478c957b439b5e4483ce1c95')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  msg "### configure"
  ./configure --prefix=/usr --sysconfdir=/etc
  msg "### make"
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  msg "### make install"
  make DESTDIR="${pkgdir}" install
  _docdir=${pkgdir}/usr/share/doc/${pkgname}
  _licdir=${pkgdir}/usr/share/licenses/${pkgname}
  install -dm755 ${_docdir} ${_licdir}
  install -Dpm644 COPYRIGHT NEWS README changes.txt doc/lesskeys.rc doc/most-fun.txt doc/most.hlp doc/most.rc ${_docdir}/
  install -Dpm644 COPYING ${_licdir}/
}
