# Maintainer: Noa Himesaka <himesaka@noa.codes>
pkgname=apple-bcm-firmware
pkgver=14.0 #monterey is macOS 12, probably change this to whatever macos version you got fw from
pkgrel=1
pkgdesc="Wi-Fi and Bluetooth Firmware from macOS Big Sur for T2 and M1 Macs"
arch=("any")
url=""
license=('unknown')
replaces=('apple-bcm-wifi-firmware')
makedepends=("python3" "tar")
source=("https://mirror.funami.tech/arch-mact2/firmware/bluetooth.tar.gz"
	"https://mirror.funami.tech/arch-mact2/firmware/wifi.tar.gz"
	"asahi-installer::git+https://github.com/NoaHimesaka1873/asahi-installer")
sha256sums=('SKIP'
            'SKIP'
            'SKIP')
build() {
    cd asahi-installer
    mkdir ../firmware-wifi
    mkdir ../firmware-bluetooth
    ls .. -l
    python3 -m asahi_firmware.wifi ../wifi ../firmware-wifi
    python3 -m asahi_firmware.bluetooth ../bluetooth ../firmware-bluetooth
}
package() {
    mkdir -p $pkgdir/usr/lib/firmware
    cd $pkgdir/usr/lib/firmware
    tar xf $srcdir/firmware-wifi/firmware.tar
    tar xf $srcdir/firmware-bluetooth/firmware.tar
}
