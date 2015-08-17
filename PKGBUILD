pkgname=qtdenter-git
pkgver=20121213
pkgrel=1
pkgdesc="Identi.ca/Status.Net client written in python and pyqt"
arch=('i686' 'x86_64')
url="http://dev.pztrn.ru/qtdenter"
license=('GPLv3')
depends=('python2' 'python2-distribute' 'python2-pyqt')
makedepends=('git')
provides=('qtdenter')

_gitroot="git://git.pztrn.ru/qtdenter.git"
_gitname="qtdenter"

build() {
    cd $srcdir

    msg "Connecting to GIT server..."
    if [[ -d ${_gitname} ]]; then
        (cd ${_gitname} && git pull origin)
    else
        git clone ${_gitroot} ${_gitname}
    fi

    msg "GIT checkout done or server timeout"
    msg "Starting make..."

    cd ${srcdir}/${_gitname}

    python2 setup.py build || exit 1
    python2 setup.py install --root="${pkgdir}" --optimize=1 || exit 1

    chmod +x ${pkgdir}/usr/bin/qtdenter

    rm -rf ${_gitname}-build
}

