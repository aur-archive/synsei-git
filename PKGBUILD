# Maintainer: Chris Sivanich <csivanich at gmail dot com>

_gitname='synsei'
_gitroot='https://github.com/csivanich/'$_gitname'.git'

pkgname=synsei-git
pkgver=r27.7bddba7
pkgrel=1
pkgdesc='Easily manage synaptics configurations'
arch=(any)
url='https://github.com/csivanich/synsei'
license=('GPLV2')
depends=('xf86-input-synaptics')
makedepends=('git')
provides=('synsei')
conflicts=('synsei')
source=("$_gitname::git+$_gitroot" "synsei-bin")
sha256sums=('SKIP' 'def0f6961f1277972f8713e2ff5b47f3c2078f4df38f9df8e11505b7a46d724e')

package() {
    cd "$srcdir/$_gitname"

    share="${pkgdir}/usr/share/${pkgname}"
    bin="${pkgdir}/usr/bin"
    docs="${pkgdir}/usr/share/docs/${pkgname}"

    mkdir -p "$share" "$bin" "$docs"

    install -Dm755 "$srcdir/../synsei-bin" "$bin"/synsei
    install -Dm644 README.md "$docs"/README.md
    install -Dm644 functions "$share"/functions
    install -Dm755 actions debug edit help list load save synsei view "$share"
    install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

pkgver() {
    cd "$_gitname"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}
