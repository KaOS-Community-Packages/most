pkgname=most
_pkgver=pre5.1-24
pkgver=$(echo ${_pkgver}|sed "s/pre//"|sed "s/\-/./")"pre"
pkgrel=1
pkgdesc="A terminal pager similar to 'more' and 'less'"
arch=('x86_64')
depends=('slang')
license=('GPL')
url="http://www.jedsoft.org/most/index.html"
install="${pkgname}.install"
source=(https://www.jedsoft.org/snapshots/${pkgname}-${_pkgver}.tar.gz)
md5sums=('a17377a6615fd1c02f24b6092b9d21f2')

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
  install -Dpm644 COPYRIGHT NEWS README changes.txt doc/lesskeys.rc doc/most-fun.txt doc/most.hlp doc/most.rc ${_docdir}/
  install -Dpm644 COPYING ${_licdir}/
}
