# Maintainer: 3ric <github.com/X3ric>
pkgname=picom-x
_gitname=picom
pkgver=1907_9.rc1.229.gf674e38_2023.06.18
pkgrel=1
pkgdesc="X compositor (fork of compton) (git-version)"
arch=(i686 x86_64)
url="https://github.com/X3ric/${_gitname}"
license=('MIT' 'MPL2')
depends=('libev' 'libgl' 'libx11' 'libxcb' 'libxext' 'pcre2' 'xcb-util' 'xcb-util-image'
         'xcb-util-renderutil' 'pixman' 'libconfig' 'libdbus' 'hicolor-icon-theme')
makedepends=('asciidoc' 'cmake' 'git' 'libglvnd' 'mesa' 'meson' 'uthash' 'xorgproto')
optdepends=('dbus:          To control picom via D-Bus'
            'python:        For picom-convgen.py'
            'xorg-xwininfo: For picom-trans'
            'xorg-xprop:    For picom-trans')
provides=('compton' 'compton-git' 'picom')
conflicts=('compton' 'compton-git' 'picom')
replaces=('compton-git')
source=(git+"https://github.com/X3ric/${_gitname}.git#branch=next")
md5sums=("SKIP")

pkgver() {
    cd ${_gitname}
    _tag=$(git describe --tags | sed 's:^v::') # tag is mobile, and switches between numbers and letters, can't use it for versioning
    _commits=$(git rev-list --count HEAD) # total commits is the most sane way of getting incremental pkgver
    _date=$(git log -1 --date=short --pretty=format:%cd)
    printf "%s_%s_%s\n" "${_commits}" "${_tag}" "${_date}" | sed 's/-/./g'
}

build() {
  cd "${srcdir}/${_gitname}"
  meson --buildtype=release . build --prefix=/usr -Dwith_docs=true
  ninja -C build
}

package() {
  cd "${srcdir}/${_gitname}"

  DESTDIR="${pkgdir}" ninja -C build install

  # install license
  install -D -m644 "LICENSES/MIT" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE-MIT"

  # example conf
  install -D -m644 "picom.sample.conf" "${pkgdir}/etc/xdg/picom.conf.example"
}
