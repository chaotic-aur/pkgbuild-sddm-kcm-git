# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Felix Yan <felixonmars@archlinux.org>
# Contributor: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=sddm-kcm-git
pkgver=5.23.80_r623.g8730a44
pkgrel=1
pkgdesc='KDE Config Module for SDDM'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(GPL)
depends=(sddm-git knewstuff-git systemsettings-git)
makedepends=(extra-cmake-modules-git kdoctools-git)
groups=(plasma-git)
source=("git+https://invent.kde.org/plasma/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

