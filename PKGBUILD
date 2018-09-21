pkgname=most
_pkgver=pre5.1-20
pkgver=5.1.20pre
pkgrel=1
pkgdesc="A terminal pager similar to 'more' and 'less'"
arch=('x86_64')
depends=('slang')
license=('GPL')
url="http://www.jedsoft.org/most/index.html"
install="${pkgname}.install"
source=(https://www.jedsoft.org/snapshots/${pkgname}-${_pkgver}.tar.gz)
md5sums=('6642b4bdce5f5d0c170168f2b03c974a')

build() {
  cd "${srcdir}/${pkgname}-${_pkgver}"
  msg "### configure"
  ./configure --prefix=/usr --sysconfdir=/etc
  msg "### make"
  make
}

package() {
  cd "${srcdir}/${pkgname}-${_pkgver}"
  msg "### make install"
  make DESTDIR="${pkgdir}" install
  _docdir=${pkgdir}/usr/share/doc/${pkgname}
  _licdir=${pkgdir}/usr/share/licenses/${pkgname}
  install -dm755 ${_docdir} ${_licdir}
  install -Dpm644 COPYRIGHT README changes.txt lesskeys.rc most-fun.txt most.doc most.hlp most.rc ${_docdir}/
  install -Dpm644 COPYING ${_licdir}/
}
