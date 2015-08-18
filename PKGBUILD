# Maintaienr:  TDY <tdy@archlinux.info>
# Contributor: nut543 <kfs1@online.no>

pkgname=xsri
pkgver=2.1.0
pkgrel=4
pkgdesc="A simple tool for setting the root window background to an image or gradient"
arch=('i686' 'x86_64')
url="http://www.pleyades.net/pawm/utilities.php"
license=('GPL')
depends=('gtk2' 'popt')
makedepends=('rpmextract')
source=(http://download.fedoraproject.org/pub/fedora/linux/releases/15/Everything/source/SRPMS/$pkgname-$pkgver-17.fc12.src.rpm)
md5sums=('3e8765a2e9356dae2242532c62d09837')

build() {
  cd "$srcdir"
  rpmextract.sh $pkgname-$pkgver-17.fc12.src.rpm
  bsdtar -xf $pkgname-$pkgver.tar.gz

  cd "$srcdir/$pkgname-$pkgver"
  sed -i '77,79d' Makefile.in
  LDFLAGS="$(pkg-config --libs x11) -lm" ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
  install -Dm644 README "$pkgdir/usr/share/doc/$pkgname/README"
  install -Dm644 "$srcdir/$pkgname.1" "$pkgdir/usr/share/man/man1/$pkgname.1"
}

# vim:set ts=2 sw=2 et:
