# Mantainer: sgar < swhaat at github >

pkgbase=esphomeyaml
pkgname=esphome
pkgver=2024.5.0
pkgrel=0
pkgdesc="Solution for your ESP8266/ESP32 projects with Home Assistant"
url="https://github.com/esphome/ESPHome"
depends=('python-setuptools'
	'python-voluptuous'
	'python-yaml'
	'python-paho-mqtt'
	'python-colorlog'
	'python-icmplib'
	'python-tornado'
	'python-tzlocal'
	'python-tzdata'
	'python-pyserial'
	'platformio-core'
	'esptool'
	'python-click'
	'python-aioesphomeapi'
	'python-zeroconf'
	'python-magic'
	'python-ruamel-yaml'
	'python-kconfiglib'
	'python-pyparsing'
	'python-argcomplete'
)
optdepends=('python-esphome-dashboard: esphome dashboard addition')
license=('MIT')
arch=('any')
replaces=('esphomeyaml')
source=("https://github.com/esphome/ESPHome/archive/${pkgver}.tar.gz")
sha256sums=('d0178a2c6823d5c2fac069acf62b592d9c5cac532289d92596d05c751c016787')

prepare() {
	cd "$srcdir/${pkgname}-${pkgver}"
	sed -i 's/==.*//' requirements.txt
}

build() {
	cd "$srcdir/${pkgname}-${pkgver}"
	python setup.py build
}

package() {
	cd "$srcdir/${pkgname}-${pkgver}"
	python setup.py install --root="$pkgdir" --optimize=1 --skip-build
}

check() {
	cd "$srcdir/${pkgname}-${pkgver}"

	##	 Run tests, takes a while
	cp ${pkgname}/__main__.py ${pkgname}.py
	#    python esphome.py tests/test1.yaml compile
	#    python esphome.py tests/test2.yaml compile
}
