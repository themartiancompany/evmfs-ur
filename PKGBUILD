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

# Maintainers:
#  Truocolo
#    <truocolo@aol.com>
#    <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#  Pellegrino Prevete (tallero)
#    <pellegrinoprevete@gmail.com>
#    <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

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
if [[ ! -v "_offline" ]]; then
  _offline="false"
fi
if [[ ! -v "_tag_name" ]]; then
  _tag_name="commit"
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="github"
fi
if [[ ! -v "_docs" ]]; then
  _docs="true"
fi
if [[ ! -v "_contracts" ]]; then
  _contracts="true"
fi
if [[ "${_git}" == "true" ]]; then
  if [[ "${_evmfs}" == "true" ]]; then
    _archive_format="bundle"
  elif [[ "${_evmfs}" == "false" ]]; then
    _archive_format="git"
  fi
elif [[ "${_git}" == "false" ]]; then
  if [[ "${_git_http}" == "gitlab" ]]; then
    _archive_format="tar.gz"
  elif [[ "${_git_http}" == "github" ]]; then
    if [[ "${_tag_name}" == "pkgver" ]]; then
      _archive_format="tar.gz"
    elif [[ "${_tag_name}" == "commit" ]]; then
      _archive_format="zip"
    fi
  fi
fi
if [[ ! -v "_solc" ]]; then
  _solc="true"
fi
if [[ ! -v "_hardhat" ]]; then
  _hardhat="true"
fi
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
pkgver="0.0.0.0.0.0.0.1.1.1"
_commit="8f9a3ffd961cc84eaa6534dc80f05a5998bb044d"
_docs_commit="a98856dc95664b9da8fc52448224c8b61dc34c23"
pkgrel=9
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
_http="https://${_git_http}.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${_pkg}"
_docs_url="${url}-docs"
license=(
  'AGPL3'
)
depends=(
  "awk"
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
_evmfs_docs_optdepends=(
  "${_pkg}-docs:"
    "EVMFS documentation and manuals."
)
_evmfs_docs_ref_optdepends=(
  "${_pkg}:"
    "package this documentation package pertains."
)
_evmfs_contracts_ref_optdepends=(
  "${_pkg}:"
    "Reference EVMFS implementation."
)
optdepends=(
  "${_evmfs_docs_optdepends[*]}"
  "${_evmfs_zenity_optdepends[*]}" 
)
if [[ "${_os}" == 'Android' ]]; then
  optdepends+=(
  )
fi
makedepends=(
  'make'
)
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    "git"
  )
fi
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
fi
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
_tarname="${_pkg}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
_docname="${_pkg}-docs-${_docs_tag}"
_docfile="${_docname}.${_archive_format}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
_gitlab_commit_sum="bd4577c7f3300aaa85d50387a8c7d95171467027c3350c9077fbc79e122a3983"
_gitlab_commit_sig_sum="ca211a4426bbb2dda33df500cb397b807142388e12f4e4d5f06d0dd2cfdd1402"
_docs_github_commit_sum="2a976cb13093cfcb23a14806ff27d1c37024be436da9f620005f4ff0c4fea729"
_docs_github_commit_sig_sum="b31adea3fb4862dbb6316acad2cb2fecf133a19d2ed3d06a019914de38714199"
_bundle_sum="SKIP"
_bundle_sig_sum="SKIP"
_github_commit_sum="fea6689e9f774defd9df21e8156aa025f01ac9de55241dd3de22fe4852cc92bd"
_github_commit_sig_sum="a43d86d8a666c1930a5b3caf16cc17f9e463970377b45c261927aa2132378878"
_github_pkgver_sum="SKIP"
_github_pkgver_sig_sum="SKIP"
# Truocolo
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_gitlab_commit_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_gitlab_commit_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
_evmfs_docs_uri="${_evmfs_dir}/${_docs_github_commit_sum}"
_evmfs_docs_src="${_docname}.zip::${_evmfs_docs_uri}"
_docs_sig_uri="${_evmfs_dir}/${_docs_github_commit_sig_sum}"
_docs_sig_src="${_docname}.zip.sig::${_docs_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_git}" == "false" ]]; then
    _src="${_evmfs_src}"
    if [[ "${_git_http}" == "github" ]]; then
      if [[ "${_tag_name}" == "pkgver" ]]; then
        _sig_src="${_github_pkgver_sig_src}"
        _sig_sum="${_github_pkgver_sig_sum}"
      elif [[ "${_tag_name}" == "commit" ]]; then
        _sig_src="${_github_commit_sig_src}"
        _sig_sum="${_github_commit_sig_sum}"
        _docs_sum="${_docs_github_commit_sum}"
        _docs_sig_sum="${_docs_github_commit_sig_sum}"
      fi
    elif [[ "${_git_http}" == "gitlab" ]]; then
      if [[ "${_tag_name}" == "commit" ]]; then
        _sig_src="${_gitlab_commit_sig_src}"
        _sig_sum="${_gitlab_commit_sig_sum}"
        _docs_sum="${_docs_gitlab_commit_sum}"
        _docs_sig_sum="${_docs_gitlab_commit_sig_sum}"
      fi
    fi
  elif [[ "${_git}" == "true" ]]; then
    _src="${_bundle_src}"
  fi
  _docs_src="${_evmfs_docs_src}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
  if [[ "${_docs}" == "true" ]]; then
    source+=(
      "${_docs_sig_src}"
    )
    sha256sums+=(
      "${_docs_sig_sum}"
    )
  fi
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_git}" == "true" ]]; then
    _uri="${_url}#${_tag_name}=${_tag}?signed"
    _docs_uri="${_docs_url}#${_tag_name}=${_docs_tag}"
    _src="${_tarname}::git+${_uri}"
    _docs_src="${_docname}::git+${_docs_uri}"
    _sum="SKIP"
    _docs_sum="SKIP"
  elif [[ "${_git}" == false ]]; then
    if [[ "${_tag_name}" == 'pkgver' ]]; then
      if [[ "${_git_http}" == "github" ]]; then
        _docs_filename="${_docs_tag}.${_archive_format}"
        _tar_filename="${_tag}.${_archive_format}"
        _uri="${_url}/archive/refs/tags/${_tar_filename}"
        _docs_uri="${_docs_url}/archive/refs/tags/${_docs_filename}"
        _sum="${_github_pkgver_sum}"
      fi
    elif [[ "${_tag_name}" == "commit" ]]; then
      if [[ "${_git_http}" == "github" ]]; then
        _tar_filename="${_commit}.${_archive_format}"
        _docs_filename="${_docs_commit}.${_archive_format}"
        _uri="${_url}/archive/${_tar_filename}"
        _docs_uri="${_docs_url}/archive/${_docs_filename}"
        _sum="${_github_commit_sum}"
      elif [[ "${_git_http}" == "gitlab" ]]; then
        _tar_filename="${_pkg}-${_tag}.${_archive_format}"
        _docs_filename="${_pkg}-docs-${_docs_tag}.${_archive_format}"
        _uri="${_url}/-/archive/${_tag}/${_pkg}-${_tar_filename}"
        _docs_uri="${_docs_url}/-/archive/${_docs_tag}/${_docs_filename}"
        _sum="${_gitlab_commit_sum}"
      fi
      _src="${_tarfile}::${_uri}"
      _docs_src="${_docfile}::${_docs_uri}"
    fi
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
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  "12D8E3D7888F741E89F86EE0FEC8567A644F1D16"
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
  rm \
    -rf \
    "${srcdir}/${_tarname}/contracts/Path"
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
  depends=()
  optdepends=(
    "${_evmfs_contracts_ref_optdepends[*]}"
  )
  _make_opts+=(
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
  install \
    -Dm644 \
    "COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

package_evmfs() {
  local \
    _make_opts=()
  depends+=(
    "${_pkg}-contracts"
  )
  _make_opts+=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
    VERBOSE=1
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-scripts
  install \
    -Dm644 \
    "COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

package_evmfs-docs() {
  local \
    _make_opts=()
  depends=()
  optdepends=(
    "${_evmfs_docs_ref_optdepends[*]}"
  )
  _make_opts+=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-doc \
    install-man
  install \
    -Dm644 \
    "COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

# vim: ft=sh syn=sh et
