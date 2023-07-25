# Maintainer: AnClark Liu <clarklaw4701@qq.com>

_pkgname=mw2fcitx
pkgname=python-$_pkgname
pkgver=3.10
pkgrel=1
pkgdesc='Build fcitx5 libraries from MediaWiki sites'
arch=('any')
url='https://github.com/outloudvi/mw2fcitx'
license=('custom')
depends=('python' 'opencc' 'pypinyin')
makedepends=('python-build' 'python-installer' 'python-hatchling' 'python-wheel')
source=("git+${url}"
"0000-add-back-manual_fix.patch"
)
sha256sums=('SKIP'
'c18b4bf7bea1c7b6482c0b3c88aa49717b27e6c4b4b3ce492c6b9e920edee3f9'
)

prepare() {
  cd "$srcdir"/$_pkgname

  patch -N -p1 -i "$srcdir"/0000-add-back-manual_fix.patch
}

build() {
  cd "$srcdir"/$_pkgname

  python -m build -nw
  #python setup.py build
}

package() {
  cd "$srcdir"/$_pkgname

  #python setup.py install --prefix "$pkgdir"
  python -m installer -d "$pkgdir" dist/*.whl

  install -Dm 644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

# vim:set ts=2 sw=2 et:
