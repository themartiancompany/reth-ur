# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
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
# Maintainer: Oliver Nordbjerg <hi@notbjerg.me>

_pkg=reth
pkgname="${_pkg}"
pkgver=1.2.0
_commit="1e965caf5fa176f244a31c0d2662ba1b590938db"
_pkgver="v${pkgver}"
pkgrel=1
pkgdesc="A fast implementation of the Ethereum protocol in Rust"
arch=(
  'x86_64'
  'i686'
  'arm'
  'aarch64'
  'armv7l'
  'mips'
  'pentium4'
)
_http="https://github.com"
_ns="paradigmxyz"
url="${_http}/${_ns}/${_pkg}"
license=(
  'MIT'
  'APACHE'
)
depends=()
makedepends=(
  'git'
  'cargo'
  'clang'
)
_tag_name="commit"
_tag="${_commit}"
source=(
  "git+${url}.git#${_tag_name}=${_tag}")
sha512sums=('SKIP')

prepare() {
  cd \
    "${_pkg}"
  export \
    RUSTUP_TOOLCHAIN="stable"
  cargo \
    fetch \
    --locked \
    --target \
    "$CARCH-unknown-linux-gnu"
}

build() {
  cd \
    "${_pkg}"
  export \
    RUSTUP_TOOLCHAIN="stable" \
    CARGO_TARGET_DIR="target"
  cargo \
    build \
    --bin \
      "${_pkg}" \
    --frozen \
    --profile \
      "maxperf" \
    --features \
      "jemalloc,asm-keccak"
}

package() {
  cd \
    "${_pkg}"
  install \
    -Dm755 \
    "target/maxperf/${_pkg}" \
    "${pkgdir}/usr/bin/${_pkg}"
  install \
    -Dm644 \
    "LICENSE-MIT" \
    "${pkgdir}/usr/share/licenses/${_pkg}/LICENSE-MIT"
  install \
    -Dm644 \
    "LICENSE-APACHE" \
    "${pkgdir}/usr/share/licenses/${_pkg}/LICENSE-APACHE"
}
