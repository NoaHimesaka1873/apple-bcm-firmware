# Maintainer: Noa Himesaka <himesaka@noa.codes>
pkgname=apple-bcm-firmware
pkgver=13.0 #monterey is macOS 12, probably change this to whatever macos version you got fw from
pkgrel=1
pkgdesc="Wi-Fi and Bluetooth Firmware from macOS Big Sur for T2 and M1 Macs"
arch=("any")
url=""
license=('unknown')
replaces=('apple-bcm-wifi-firmware')
makedepends=("python3" "tar")
source=("https://mirror.funami.tech/arch-mact2/firmware/bluetooth.tar.gz"
	"https://mirror.funami.tech/arch-mact2/firmware/wifi.tar.gz"
	"asahi-installer::git+https://github.com/AsahiLinux/asahi-installer#commit=d08345d94194dc810319172871a9ba06f77da9bd")
sha256sums=('SKIP'
            'SKIP'
            'SKIP')
build() {
    cd asahi-installer/src
    python3 -m asahi_firmware.wifi ../../wifi ../../firmware-wifi.tar
    python3 -m asahi_firmware.bluetooth ../../bluetooth ../../firmware-bluetooth.tar
}
package() {
    mkdir -p $pkgdir/usr/lib/firmware
    cd $pkgdir/usr/lib/firmware
    tar xf $srcdir/firmware-wifi.tar
    tar xf $srcdir/firmware-bluetooth.tar
}
