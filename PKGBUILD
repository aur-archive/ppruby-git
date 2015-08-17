pkgname=ppruby-git
pkgver=0.9.2.2.1
pkgrel=1
pkgdesc="Ruby binding units for FreePascal"
url="https://github.com/shikhalev/ppruby"
license=("GPLv3")
arch=(i686 x86_64)
depends=(fpc)
makedepends=(fpc git)
source=("${pkgname%-*}::git+https://github.com/shikhalev/ppruby.git")
md5sums=('SKIP')

_unittgt=`fpc -iSP`-`fpc -iSO`
_fpcver=`fpc -iV`

pkgver () {
	cd "$srcdir/${pkgname%-*}"
	git describe | sed 's|\(.*-.*\)-.*|\1|;s|-|.|'
}

build() {
	cd "${srcdir}/${pkgname%-*}/static"
	fpc ruby18.pp
}

package() {
	cd "${srcdir}/${pkgname%-*}/static"
	find . -name '*.o' -o -name '*.ppu' -o -name '*.rst' -o -name '*.a' |
		xargs -rtl1 -I {} install -Dm644 {} "$pkgdir/usr/lib/fpc/$_fpcver/units/$_unittgt/ppruby/"{}
}
