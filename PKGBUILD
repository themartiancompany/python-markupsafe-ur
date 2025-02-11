# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Maintainer : Felix Yan <felixonmars@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Alex Anthony <alex.anthony28991@gmail.com>

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
sha512sums=(
  'SKIP'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    "setup.py" \
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
    "setup.py" \
      install \
        --root="${pkgdir}" \
	--optimize=1
  install \
    -Dm644 \
      "LICENSE.rst" \
    -t \
      "${pkgdir}/usr/share/licenses/${pkgname}/"
}

# vim:set sw=2 sts=-1 et:
