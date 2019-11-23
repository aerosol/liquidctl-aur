pkgname=('python-liquidctl')
_module='liquidctl'
pkgver='1.3.1'
pkgrel=1
pkgdesc="Cross-platform tool and drivers for liquid coolers and other devices"
url="https://github.com/jonasmalacofilho/liquidctl"
depends=('python' 'python-setuptools' 'python-pyusb' 'python-hidapi' 'python-docopt')
makedepends=()
license=('GPL3')
arch=('any')
source=("https://files.pythonhosted.org/packages/source/l/liquidctl/liquidctl-${pkgver}.tar.gz")
sha256sums=('6092a6fae477908c80adc825b290e39f0b26e604593884da23d40e892e553309')

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
    install -Dm644 liquidctl.8 "${pkgdir}/usr/share/man/man8/liquidctl.8"
}
