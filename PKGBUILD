# $Id: PKGBUILD,v 1.12 2003/11/06 08:26:13 dorphell Exp $
# Maintainer: Marty_Stoopid <>
# Contributor: Marty_Stoopid <>
pkgname=kstm
pkgver=0.1
pkgrel=3
pkgdesc="KDE front-end to ssh tunneling"
arch=('i686' 'x86_64')
url="http://sourceforge.net/projects/kstm/"
license=('GPL3')
depends=('qt4' 'ksshaskpass' 'openssh')
makedepends=('qt4' 'make' 'sed')
install=kstm.install
source=(http://downloads.sourceforge.net/sourceforge/kstm/kstm$pkgver-source.tar.gz
		 kstm.desktop
)
md5sums=('5f5d82dda7961f7595582fa51f7e4e8e'
		      '0200c7e2a25c24127160d6df9a72b4ae'
)

build() {
# Install the icon
  install -Dm644 $startdir/src/kstm/icons/kstm_64x64.png "${pkgdir}/usr/share/pixmaps/kstm.png"
# Install the .desktop file
  install -Dm644 kstm.desktop "${pkgdir}/usr/share/applications/kstm.desktop"
  cd $startdir/src/kstm
  sed -i 's/icons\/kstm\.png/:icons\/icons\/kstm.png/g' mainwindow.cpp
  qmake-qt4 || return 1
  make || return 1
  install -Dm755 kstm $pkgdir/usr/bin/kstm
}
