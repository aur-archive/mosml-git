# Maintainer: Earnestly <zibeon@gmail.com>

pkgname=mosml-git
pkgver=2.10.1.r7.g96407bc
pkgrel=1
epoch=1

pkgdesc='Moscow ML is a light-weight implementation of Standard ML (SML)'
url='http://www.itu.dk/~sestoft/mosml.html'
arch=('i686' 'x86_64')
license=('GPL')

depends=('glibc')
makedepends=('git')

provides=('mosml')
conflicts=('mosml')

source=('git://github.com/kfl/mosml')

md5sums=('SKIP')

pkgver() {
    cd mosml
    git describe --tags | sed 's/^ver-//; s/-/.r/; s/-/./'
}

build() {
    cd mosml/src
    make BINDIR=/usr/bin LIBDIR=/usr/lib/mosml world
}

package() {
    cd mosml/src
    make PREFIX=/usr DESTDIR="$pkgdir" install

    # This isn't done by the Makefile
    cd ../man
    for manual in *.1; do
        install -Dm644 "$manual" "$pkgdir"/usr/share/man/man1/"$manual"
    done
}
