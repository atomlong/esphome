# Mantainer: sgar < swhaat at github >

pkgbase=esphomeyaml
pkgname=esphome
pkgver=2024.5.2
pkgrel=0
pkgdesc="Solution for your ESP8266/ESP32 projects with Home Assistant"
url="https://github.com/esphome/ESPHome"
depends=('python-build' 'python-installer' 'python-wheel'
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
sha256sums=('6562fab0d0f994d8a17c5bf3cef1d50ef217536cf8704ddb8f630354564b9f84')

prepare() {
	cd "$srcdir/${pkgname}-${pkgver}"
	sed -i 's/==.*//' requirements.txt
}

build() {
	cd "$srcdir/${pkgname}-${pkgver}"
        python -m build --wheel --no-isolation
}

package() {
	cd "$srcdir/${pkgname}-${pkgver}"
        python -m installer --destdir="$pkgdir" dist/*.whl
}

check() {
	cd "$srcdir/${pkgname}-${pkgver}"

	##	 Run tests, takes a while
	cp ${pkgname}/__main__.py ${pkgname}.py
	#    python esphome.py tests/test1.yaml compile
	#    python esphome.py tests/test2.yaml compile
}
