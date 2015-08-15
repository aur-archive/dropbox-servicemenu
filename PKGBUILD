# Maintainer: (locke87) Felix Mauch
# based on http://kde-apps.org/content/show.php?content=124416

pkgname=dropbox-servicemenu
pkgver=0.16.1
pkgrel=2
pkgdesc="A servicemenu for KDE4 which allows easy access to most of Dropbox features. It uses Dropbox CLI to generate public urls, and pyndexer to allow sharing directories in public directory."
url="http://kde-apps.org/content/show.php?content=124416"
license=('GPL')
arch=(any)
depends=('dropbox' 'python2' 'kdebase-kdialog' 'python-m2crypto' 'sharutils' 'recode' 'perl')
source=(http://kde-look.org/CONTENT/content-files/124416-DropboxServiceMenu-${pkgver}.tar.gz)
md5sums=('3c0186649311611abfbb8ac016a67791')

 
build() {
	cd "$srcdir/DropboxServiceMenu-${pkgver}/"

  sed -i 's/#!\/usr\/bin\/python/#!\/usr\/bin\/python2/' dropbox-scripts/dropbox.py
  sed -i 's/#!\/usr\/bin\/python/#!\/usr\/bin\/python2/' dropbox-scripts/dropbox-notify.py
  sed -i 's/#!\/usr\/bin\/env python/#!\/usr\/bin\/env python2/' dropbox-scripts/pyndexer.py
  sed -i 's/python/python2/' dropbox-scripts/dropbox_menu.sh
  sed -i 's/localprefix/prefix/' dropbox_all.desktop
  sed -i 's/localprefix/prefix/' dropbox_files.desktop
  sed -i 's/localprefix/prefix/' dropbox_directories.desktop
  sed -i 's/localprefix`/prefix`\//' dropbox-scripts/dropbox_menu.sh

	mkdir -p ${pkgdir}/"`kde4-config --prefix`/share/kde4/services/ServiceMenus/"
	mkdir -p ${pkgdir}/"`kde4-config --prefix`/share/kde4/services/ServiceMenus/dropbox-scripts/"	
	mkdir -p ${pkgdir}/"/usr/bin/"
	install -m 755 dropbox-scripts/* ${pkgdir}/"`kde4-config --prefix`/share/kde4/services/ServiceMenus/dropbox-scripts/"
  install -m 644 dropbox_all.desktop ${pkgdir}/"`kde4-config --prefix`/share/kde4/services/ServiceMenus/"
  install -m 644 dropbox_files.desktop ${pkgdir}/"`kde4-config --prefix`/share/kde4/services/ServiceMenus/"
  install -m 644 dropbox_directories.desktop ${pkgdir}/"`kde4-config --prefix`/share/kde4/services/ServiceMenus/"
} 
