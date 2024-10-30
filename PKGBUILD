# SPDX-License-Identifier: AGPL-3.0
# 
# Maintainer : Felix Yan <felixonmars@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Alex Anthony <alex.anthony28991@gmail.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=markupsafe
pkgname="${_py}-${_pkg}"
pkgver=2.1.4
_commit="b7cd6523579ea5a08d89799f2a64ec2c2bc45eca"
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
license=(
  'BSD'
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  'git'
  "${_py}-setuptools"
)
checkdepends=(
  "${_py}-pytest"
)
_http="https://github.com"
_ns="pallets"
_url="${_http}/${_ns}/${_pkg}"
source=(
  "${_pkg}-${pkgver}::git+${_url}.git#commit=${_commit}"
)
sha512sums=('SKIP')

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      build
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
  PYTHONPATH=src \
  pytest
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      install \
        --root="${pkgdir}" \
	--optimize=1
  install \
    -Dm644 \
      LICENSE.rst \
    -t \
      "${pkgdir}/usr/share/licenses/${pkgname}/"
}

# vim:set sw=2 sts=-1 et:
