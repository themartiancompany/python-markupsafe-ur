# SPDX-License-Identifier: AGPL-3.0
# 
# Maintainer : Felix Yan <felixonmars@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Alex Anthony <alex.anthony28991@gmail.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>

pkgname=python-markupsafe
pkgver=2.1.4
_commit=b7cd6523579ea5a08d89799f2a64ec2c2bc45eca
pkgrel=1
pkgdesc="Implements a XML/HTML/XHTML Markup safe string for Python"
arch=(
  'x86_64'
  'arm'
  'aarch64'
  'powerpc'
  'i686'
  'pentium4'
  'armv7h'
)
url="https://pypi.python.org/pypi/MarkupSafe"
license=('BSD')
depends=(
  'python'
)
makedepends=(
  'git'
  'python-setuptools'
)
checkdepends=(
  'python-pytest'
)
source=(
  "git+https://github.com/pallets/markupsafe.git#commit=$_commit"
)
sha512sums=('SKIP')

build() {
  cd markupsafe
  python setup.py build
}

check() {
  cd markupsafe
  PYTHONPATH=src pytest
}

package() {
  cd markupsafe
  python \
    setup.py \
      install \
        --root="${pkgdir}" \
	--optimize=1
  install \
    -Dm644 \
      LICENSE.rst \
    -t \
      "$pkgdir"/usr/share/licenses/$pkgname/
}

# vim:set sw=2 sts=-1 et:
