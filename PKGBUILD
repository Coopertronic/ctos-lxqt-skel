# Maintainer: Matthew Phillip Cooper <matthew@coopertronic.co.uk>
pkgname=ctos-lxqt-skel
_destname1="/etc"
pkgver=1.r1
pkgrel=1
pkgdesc="Adds the default CTOS skel for LXQT."
arch=('any')
url="https://github.com/Coopertronic/ctos-lxqt-skel.git"
license=('GPL3')
makedepends=('git' 'go-md2man')
#depends=('git' 'ctos-functions' 'git-helper' 'sshpass')
conflicts=()
provides=("${pkgname}")
options=(!strip !emptydirs)
source=("git+$url")
sha256sums=('SKIP')

pkgver() {
    cd "${srcdir}/${pkgname}"
    printf "1.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
    ##  Install Scripts
    install -dm755 ${pkgdir}${_destname1}
    cp -r ${srcdir}/${pkgname}${_destname1}/* ${pkgdir}${_destname1}

    ##  Install documentation
    install -d $pkgdir/usr/share/man/man1
    install -d $pkgdir/usr/share/doc/$pkgname
    go-md2man -in $srcdir/$pkgname/README.md -out $srcdir/$pkgname/$pkgname.1
    install -D -m644 $srcdir/$pkgname/$pkgname.1 $pkgdir/usr/share/man/man1/$pkgname.1
    install -D -m644 $srcdir/$pkgname/README.md $pkgdir/usr/share/doc/$pkgname/README.md
}
