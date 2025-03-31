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
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_os="$( \
  uname \
    -o)"
_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_offline="false"
_git="false"
_docs="true"
if [[ ! -v "_contracts" ]]; then
  _contracts="true"
fi
_solc="true"
_hardhat="true"
_proj="hip"
_py="python"
_pkg=evmfs
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
if [[ "${_contracts}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-contracts"
  )
fi
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-docs"
  )
fi
pkgver="0.0.0.0.0.0.0.1.1.1.1.1.1"
_commit="ff5d0d253a773cf9530aa2aafae70f2943aba9ec"
_commit="f57a842c93ea025f834b2c48cbda60982eb77799"
_docs_commit="a98856dc95664b9da8fc52448224c8b61dc34c23"
pkgrel=1
_pkgdesc=(
  "Reference implementation of the"
  "Ethereum Virtual Machine file system (EVMFS),"
  "the internet uncensorable, unalterable,"
  "undeletable, distributed, unstoppable"
  "file system and network protocol."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${_pkg}"
_docs_url="${url}-docs"
license=(
  'AGPL3'
)
depends=(
  "evm-contracts-tools"
  "evm-wallet"
  "encoding-tools"
  "libcrash-bash"
  "libcrash-js"
  "libevm"
  "node-run"
)
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  depends+=(
  )
fi
_evmfs_zenity_optdepends=(
  "evmfs-zenity:"
    "simple graphical"
    "interface front-end written"
    "in Bash with Zenity."
)
optdepends=(
  "${_evmfs_zenity_optdepends[*]}" 
)
if [[ "${_os}" == 'Android' ]]; then
  optdepends+=(
  )
fi
makedepends=(
  'make'
)
if [[ "${_docs}" == "true" ]]; then
  makedepends+=(
    "${_py}-docutils"
  )
fi
if [[ "${_contracts}" == "true" ]]; then
  makedepends+=(
    'evm-make'
  )
  if [[ "${_solc}" == "true" ]]; then
    makedepends+=(
      "solidity=0.7.5"
      "solidity=0.8.24"
      "solidity=0.8.28"
    )
  fi
  if [[ "${_hardhat}" == "true" ]]; then
    makedepends+=(
      "hardhat"
    )
  fi
fi
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
_url="${url}"
_tag="${_commit}"
_docs_tag="${_docs_commit}"
_tag_name="commit"
_tarname="${_pkg}-${_tag}"
_docname="${_pkg}-docs-${_docs_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
_archive_sum="058ec3abe415af84dd22296fb40df3040d57bb5570db73b2b815191e9456b98c"
_evmfs_archive_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sum}"
_evmfs_archive_src="${_tarname}.zip::${_evmfs_archive_uri}"
_archive_sig_sum="4f7ee768ae1d944786b043129a565a81a6854af3ee7137171d31edfa4ca50f77"
_archive_sig_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sig_sum}"
_archive_sig_src="${_tarname}.zip.sig::${_archive_sig_uri}"
_docs_sum="2a976cb13093cfcb23a14806ff27d1c37024be436da9f620005f4ff0c4fea729"
_evmfs_docs_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_docs_sum}"
_evmfs_docs_src="${_docname}.zip::${_evmfs_docs_uri}"
_docs_sig_sum="b31adea3fb4862dbb6316acad2cb2fecf133a19d2ed3d06a019914de38714199"
_docs_sig_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_docs_sig_sum}"
_docs_sig_src="${_docname}.zip.sig::${_docs_sig_uri}"
if [[ "${_evmfs}" == true ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_archive_src}"
  _sum="${_archive_sum}"
  _docs_src="${_evmfs_docs_src}"
  source+=(
    "${_archive_sig_src}"
  )
  sha256sums+=(
    "${_archive_sig_sum}"
  )
  if [[ "${_docs}" == "true" ]]; then
    source+=(
      "${_docs_sig_src}"
    )
    sha256sums+=(
      "${_docs_sig_sum}"
    )
  fi
elif [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  _sum="SKIP"
  _docs_src="${_docname}::git+${_docs_url}#${_tag_name}=${_docs_tag}"
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum="d4f4179c6e4ce1702c5fe6af132669e8ec4d0378428f69518f2926b969663a91"
    _docs_src="${_docname}.tar.gz::${_docs_url}/archive/refs/tags/${_docs_tag}.tar.gz"
    _sum="Who cares, fetching stuff using tags with git is unsecure."
  elif [[ "${_tag_name}" == "commit" ]]; then
    _src="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="${_archive_sum}"
    _docs_src="${_docname}.zip::${_docs_url}/archive/${_docs_commit}.zip"
  fi
fi
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
if [[ "${_docs}" == "true" ]]; then
  source+=(
    "${_docs_src}"
  )
  sha256sums+=(
    "${_docs_sum}"
  )
fi

validpgpkeys=(
  # Truocolo <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
  # Truocolo (kf) <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
)

prepare() {
  cd \
    "${_tarname}"
  if [[ "${_docs}" == "true" ]]; then
    if [[ "${_git}" == "true" ]]; then
      git \
        submodule \
          init
      git \
        submodule \
          set-url \
            "docs" \
            "${srcdir}/${_docname}"
      git \
        -c \
          protocol.file.allow="always" \
        -c \
          protocol.allow="never" \
        submodule \
          update
    elif [[ "${_git}" == "false" ]]; then
      rm \
        -rf \
        "docs" || \
        true
      cp \
        -r \
        "${srcdir}/${_docname}" \
        "docs"
    fi
  fi
}

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

build() {
  cd \
    "${_tarname}"
  if [[ "${_contracts}" == "true" ]]; then
    if [[ "${_solc}" == "true" ]]; then
      SOLIDITY_COMPILER_BACKEND="solc" \
      make \
        all
    fi
    if [[ "${_hardhat}" == "true" ]]; then
      SOLIDITY_COMPILER_BACKEND="hardhat" \
      make \
       all
    fi
  fi
}

package_evmfs-contracts() {
  local \
    _make_opts=()
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-contracts
  if [[ "${_solc}" == "true" ]]; then
    make \
      "${_make_opts[@]}" \
      install-contracts-deployments-solc
  fi
  if [[ "${_hardhat}" == "true" ]]; then
    make \
      "${_make_opts[@]}" \
      install-contracts-deployments-hardhat
  fi
}

package_evmfs() {
  local \
    _make_opts=()
  depends+=(
    "${_pkg}-contracts"
  )
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-scripts
}

package_evmfs-docs() {
  local \
    _make_opts=()
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-doc
  make \
    "${_make_opts[@]}" \
    install-man
}

# vim: ft=sh syn=sh et
