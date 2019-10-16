pkgname=('python-liquidctl')
_module='liquidctl'
pkgver='1.2.0'
pkgrel=2
pkgdesc="Cross-platform tool and drivers for liquid coolers and other devices"
url="https://github.com/jonasmalacofilho/liquidctl"
depends=('python' 'python-setuptools' 'python-pyusb' 'python-hidapi' 'python-docopt' 'python-appdirs')
makedepends=()
license=('GPL3')
arch=('any')
source=(
    "https://files.pythonhosted.org/packages/source/l/liquidctl/liquidctl-${pkgver}.tar.gz"
    'liquidctl.8'
)
sha256sums=(
    'ad8c03c0695620fedaec11e7a8286bb5d4da18ba0c71e55888bfa06f8f7d7529'
    '98d3ec8959c7b36ae9c94525d94b36c37a4f7112811b34713d3dc9b792e81ea6'
)

build() {
    cd "${srcdir}/${_module}-${pkgver}"
    export DIST_NAME="$(source /etc/os-release && echo $PRETTY_NAME)"
    export DIST_PACKAGE="$pkgname $pkgver-$pkgrel"
    python setup.py build
}

package() {
    depends+=()
    cd "${srcdir}/${_module}-${pkgver}"
    python setup.py install --root="${pkgdir}" --optimize=1 --skip-build
    install -Dm644 ../liquidctl.8 "${pkgdir}/usr/share/man/man8/liquidctl.8"
}
