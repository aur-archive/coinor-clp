# Maintainer: spider-mario <spidermario@free.fr>
# Contributor: Daniel Ehlers <danielehlers@mindeye.net>
pkgname=coinor-clp
pkgver=1.15.11
pkgrel=1
pkgdesc="COIN-OR linear programming solver"
arch=('i686' 'x86_64')
url="https://projects.coin-or.org/Clp"
license=('EPL')
groups=('coinor')
depends=('coinor-osi' 'zlib' 'bzip2' 'lapack')
source=("http://www.coin-or.org/download/source/Clp/Clp-${pkgver}.tgz")
sha1sums=('16f8d889a3f37917b2d2c40371dfc6af1e590efd')

build() {
  cd Clp-$pkgver
  COIN_SKIP_PROJECTS="Sample" \
  ./configure --prefix=/usr \
              --with-osi-lib="$(pkg-config --libs osi)" \
              --with-osi-incdir="/usr/include/coin/" \
              --with-coinutils-lib="$(pkg-config --libs coinutils)" \
              --with-coinutils-incdir="/usr/include/coin/" -C
  make
}

check() {
  cd Clp-$pkgver
  make test
}

package() {
  cd Clp-$pkgver
  PKG_CONFIG_LIBDIR="$pkgdir"/usr/lib/pkgconfig/ \
  make DESTDIR="$pkgdir"/ install
}
