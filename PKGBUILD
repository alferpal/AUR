# Maintainer: Alexandre Ferrando <alferpal@gmail.com>

pkgname=iojs
pkgver=2.3.0
_foldername=iojs-v${pkgver}
pkgrel=1
pkgdesc='Evented I/O for V8 JavaScript - Node.js fork'
url='http://iojs.org/'
license=('MIT')
arch=('i686' 'x86_64')
depends=('openssl' 'zlib')
makedepends=('python2' 'git')
optdepends=('npm: nodejs package manager')
provides=('nodejs')
conflicts=('nodejs' 'iojs-bin')
options=('!emptydirs')
source=("https://iojs.org/dist/v${pkgver}/iojs-v${pkgver}.tar.gz")
install=iojs.install
sha256sums=('556e1a2f58c993fcb7a89c55bc2a4da6fba74cd4d444777a8b64b19d57c4cc3c')

prepare() {

  cd "${srcdir}/${_foldername}"

  msg "preparing python version"

  find -type f -exec sed \
    -e 's_^#!/usr/bin/env python$_&2_' \
    -e 's_^\(#!/usr/bin/python2\).[45]$_\1_' \
    -e 's_^#!/usr/bin/python$_&2_' \
    -e 's_^\( *exec \+\)python\( \+.*\)$_\1python2\2_'\
    -e 's_^\(.*\)python\( \+-c \+.*\)$_\1python2\2_'\
    -e "s_'python'_'python2'_" -i {} \;
  find test/ -type f -exec sed 's_python _python2 _' -i {} \;
}

build() {
  cd "${srcdir}/${_foldername}"

  export PYTHON=python2
  ./configure \
    --prefix=/usr \
    --shared-openssl \
    --shared-zlib \
    --with-intl=system-icu \
    --without-npm 
  make
}

check() {
  cd "${_foldername}"
  make test || warning "Tests failed"
}

package() {
  cd "${srcdir}/${_foldername}"
  make DESTDIR="$pkgdir" install

  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/iojs/LICENSE
}
