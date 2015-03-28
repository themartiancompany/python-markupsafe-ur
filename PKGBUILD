# Maintainer : Felix Yan <felixonmars@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Alex Anthony <alex.anthony28991@gmail.com>

pkgname=('python-markupsafe' 'python2-markupsafe')
pkgver=0.23
pkgrel=2
pkgdesc="Implements a XML/HTML/XHTML Markup safe string for Python"
arch=('i686' 'x86_64')
url="http://pypi.python.org/pypi/MarkupSafe"
license=('custom')
makedepends=('python-setuptools' 'python2-setuptools')
source=("http://pypi.python.org/packages/source/M/MarkupSafe/MarkupSafe-${pkgver}.tar.gz")
sha512sums=('4f1fd91ced5e7119584b56cf7b69cfe6fdd9613bd77412368a38e9ef5d1011ba5c76d1d3a0da3d60f9f474627e6c8c8b613a80a668b32d212f09072f8b1f5b28')

prepare() {
  cp -a MarkupSafe-${pkgver} python2-MarkupSafe-${pkgver}
}

build() {
  cd "${srcdir}/MarkupSafe-${pkgver}"
  python setup.py build

  cd "${srcdir}/python2-MarkupSafe-${pkgver}"
  python2 setup.py build
}

check() {
  cd "${srcdir}/MarkupSafe-${pkgver}"
  python setup.py test

  cd "${srcdir}/python2-MarkupSafe-${pkgver}"
  python2 setup.py test
}

package_python-markupsafe() {
  depends=('python')

  cd MarkupSafe-${pkgver}
  python setup.py install --root="${pkgdir}" --optimize=1

  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/python-markupsafe/LICENSE"
}

package_python2-markupsafe() {
  depends=('python2')

  cd python2-MarkupSafe-${pkgver}
  python2 setup.py install --root="${pkgdir}" --optimize=1

  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/python2-markupsafe/LICENSE"
}
