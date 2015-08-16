# Maintainer: Ngo Huy <huynhok.uit@vnoss.org>
#
# Contributor: Nguyen Ha Duong <cmpitg@gmail.com>
# Contributor: Ngo Trung <ndtrung4419@gmail.com>
# Contributor: Dam Tien Long <longdt90@gmail.com>

pkgname="ibus-bogo-git"
pkgver=0.0.0
pkgrel=1
pkgdesc="Vietnamese input method for IBus. \
Stable version's is https://aur.archlinux.org/packages/ibus-bogo/"
license=('GPL v3')
url="https://github.com/BoGoEngine/ibus-bogo-python"

arch=('any')
depends=('ibus' 'python' 'python-gobject' 'libwnck3' 'python-pyqt4' 'libnotify' 'qt4')
makedepends=('git' 'cmake' 'gcc' 'pyqt4-common')
provides=('ibus-bogo')
conflicts=('ibus-bogo')

source=('ibus-bogo-git::git+https://github.com/BoGoEngine/ibus-bogo-python.git#branch=develop')
md5sums=('SKIP')

pkgver() {
    cd "${srcdir}/${pkgname}"
    git describe --long | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
}

build()  {
    cd "${srcdir}/${pkgname}"
    
    msg "Starting make..."
            
    # Building ibus-bogo-python
    
    git submodule init
    git submodule update
        
    mkdir -p build
    cd build
        
    cmake -DCMAKE_INSTALL_PREFIX:PATH="${pkgdir}/usr" ..
    make
}

package() {
    cd "${srcdir}/${pkgname}/build"
    make install
}


