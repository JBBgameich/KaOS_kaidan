pkgname=kaidan-git
pkgver=r299.8b4fc2d
pkgrel=1
pkgdesc="Simple and user-friendly Jabber/XMPP client for every device"
arch=('x86_64')
url="https://github.com/KaidanIM/Kaidan"
license=('GPL3')
depends=('qt5-base' 'qt5-declarative' 'qt5-quickcontrols2' 'kirigami' 'gloox')
makedepends=('git' 'cmake')
source=("kaidan::git+https://github.com/KaidanIM/Kaidan")
sha256sums=('SKIP')
provides=('kaidan')

pkgver() {
  cd "$srcdir/kaidan"
  printf "r%d.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  cd "$srcdir/kaidan"
  mkdir -p build
}

build() {
  cd "$srcdir/kaidan/build"
  cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr -DI18N=ON ..
  make
}

package() {
  cd "$srcdir/kaidan/build"
  make DESTDIR="$pkgdir/" install
}
