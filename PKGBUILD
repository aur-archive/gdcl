# Maintainer  : Fernando "Firef0x" G.P. da Silva <firefgx { aT ) gmail [ d0t } com>
# Contributor : Fernando "Firef0x" G.P. da Silva <firefgx { aT ) gmail [ d0t } com>

pkgname=gdcl
pkgdesc="GoldenDict command-line interface written in Ruby, as an alternative to the StarDict Console Version(sdcv)"
pkgver=20150417.b7482c9
pkgrel=1
arch=("any")
url="https://github.com/dohliam/gdcl"
license=("MIT")
backup=('etc/xdg/gdcl/config.yml')
depends=('mplayer' 'ruby-nokogiri')
makedepends=('git')
source=("git+https://github.com/dohliam/${pkgname}.git")
sha256sums=('SKIP')

pkgver() {
  cd "${pkgname}"
  ( set -o pipefail
  printf "%s.%s" "$(git log -1 --pretty=format:%cd --date=short | sed 's/-//g')" "$(git rev-parse --short HEAD)"
  )
}

package() {
  cd "${pkgname}"

  # Patch for executable name
  sed -i -e 's|gdcl.rb|gdcl|g' \
    -e 's|# ruby|#|g' gdcl.rb

  # Install bin file
  install -Dm755 gdcl.rb "${pkgdir}/usr/bin/gdcl"

  # Install config file
  install -Dm644 config.yml "${pkgdir}/etc/xdg/${pkgname}/config.yml"

  # Install documentation
  install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"

  # Install license file
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set sts=2 sw=2 ts=2 et:
