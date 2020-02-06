_pkgname=GPXSee
pkgname=gpxsee
pkgver=7.20
pkgrel=1
pkgdesc='GPS log file viewer and analyzer'
arch=(x86_64)
url='https://www.gpxsee.org/'
screenshot='https://www.gpxsee.org/gallery/lin1.png'
license=('GPL3')
depends=('qt5-base' 'openssl' 'zstd')
makedepends=('qt5-tools' 'gcc')
optdepends=('qt5-imageformats: Support for GeoTIFF images'
            'qt5-pbfimageplugin: Support for PBF vector maps')
conflicts=(${pkgname}-git)
source=("https://ufpr.dl.sourceforge.net/project/gpxsee/Source/GPXSee-${pkgver}.tar.gz")
md5sums=('1db4614927b4fcb7175cefda12aee456')

build() {
  cd ${srcdir}/${_pkgname}-${pkgver}
  msg "### configure"
  lrelease-qt5 gpxsee.pro
  qmake-qt5 PREFIX=/usr gpxsee.pro
  msg "### make"
  make
}

package() {
  cd ${srcdir}/${_pkgname}-${pkgver}
  msg "### make install"
  make INSTALL_ROOT="${pkgdir}" install
  _docdir=${pkgdir}/usr/share/doc/${pkgname}
  _licdir=${pkgdir}/usr/share/licenses/${pkgname}
  install -dpm755 ${_docdir} ${_licdir}
  install -Dpm644 CONTRIBUTING.md README.md ${_docdir}/
  install -Dpm644 licence.txt ${_licdir}/
}
