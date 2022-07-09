#!/bin/bash

# Based on original packaging by Felix Yan <felixonmars@archlinux.org> and Bruno Pagani <archange@archlinux.org>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/spirv-headers/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/spirv-headers/discussions>

_relname=SPIRV-Headers

pkgname=spirv-headers
# epoch=1
pkgver=1.3.216.0
pkgrel=1
pkgdesc="SPIR-V Headers"
arch=(
  "any"
)
url="https://www.khronos.org/registry/spir-v/"
license=(
  "MIT"
)
makedepends=(
   # Official Arch Linux
  "cmake"
)

_tarname="${_relname}-sdk-${pkgver}"
source=(
  "${_tarname}.tar.gz"::"https://github.com/KhronosGroup/${_relname}/archive/refs/tags/sdk-${pkgver}.tar.gz"
)

# source=(
#   https://github.com/KhronosGroup/${_relname}/archive/refs/tags/sdk-${pkgver}/${pkgname}-${pkgver}.tar.gz
# )
sha512sums=(
  '951715cf62a643bfce6a3854f2206b95dd65e60b27355a2f290e829da0f06e19877e9dfcbf53f455b8a0524fb851a851742f3e16bb29be2f470cd62d3a8fc8f0'
)

build() {

  cmake -B build -S ${_relname}-sdk-${pkgver} -DCMAKE_INSTALL_PREFIX=/usr .

  make -C build
}

package() {

  make -C build DESTDIR="${pkgdir}" install

  install -Dm644 ${_relname}-sdk-${pkgver}/LICENSE -t "${pkgdir}"/usr/share/licenses/${pkgname}/
}
