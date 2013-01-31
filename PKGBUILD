# Contributor: Joeny Ang <ang(dot)joeny(at)gmail(dot)com>
# Contributor: Guan 'kuno' Qing <neokuno(at)gmail(dot)com>
# Contributor: Guten Ye <ywzhaifei(at)gmail(dot)com>
# Contributor: i_magnific0 <i_magnific0(at)yahoo(dot)com> (patch 2001)

pkgname=font-manager
pkgver=0.5.7
pkgrel=4
pkgdesc="A font management application for the GNOME desktop"
url="http://code.google.com/p/font-manager/"
arch=('i686' 'x86_64')
license=('GPL')
depends=('pygtk>=2.0' 'libxml2' 'fontconfig')
optdepends=('file-roller: to export font collections to archives'
            'gucharmap: to view selected font using GNOME character map application'
            'python-reportlab: to create PDF sample sheets')
source=(http://font-manager.googlecode.com/files/${pkgname}-${pkgver}.tar.bz2
        0001-nonexistent_cache.patch
        1001-gcc47.patch
  2001-paths.patch)
md5sums=('7cd3b635eaddcb84a8b31509880510ed'
         '50e732de1a92bc498d4cffd39185225c'
         '727acfbbce4ab8d05078e4719443ce29'
         '8dbbbb72f3f3d931d0f3a25c1a00dc85')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}
  ./configure --prefix=/usr --sysconfdir=/etc
  sed -i -e 's/^PYTHON.*/PYTHON=\/usr\/bin\/python2/' Makefile

  # apply patches from Debian
  # source: http://ftp.de.debian.org/debian/pool/main/f/font-manager/font-manager_0.5.7-4.debian.tar.gz
  patch -Np1 < ../0001-nonexistent_cache.patch
  patch -Np1 < ../1001-gcc47.patch
  patch -Np1 < ../2001-paths.patch

  # build
  make
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}
  make DESTDIR=${pkgdir}/ install
}
