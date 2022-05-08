# Maintainer: Gian Borcillo <borcillofg2020@gmail.com>

_pkgbase=mt7601u
_pkgkernelver=5.17.5
_pkgcurkernver=5.15.36-1-lts
pkgname=ralink-mt7601u
pkgver=1.0.0
pkgrel=1
pkgdesc="MT7601u fixed module"
arch=('x86_64')
url="https://github.com/gianxddddd/linux-fixes"
license=('UNLICENSED')
optdepends=('usb_modeswitch: To switch USB dongle mode from being a flash drive')
conflicts=("${_pkgbase}" "ralink-mt7601u-dkms" "mt7601u-ap-dkms" "mt7601u-firmware")
source=("https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-${_pkgkernelver}.tar.xz" "vnd_reset.patch")
sha256sums=("9bbcd185b94436f9c8fe977fa0e862f60d34003562327fcebb27c9fa342fe987" "SKIP")

prepare() {
        echo "Patching module sources for vnd_reset..."
        cd ${srcdir}/linux-${_pkgkernelver}/drivers/net/wireless/mediatek/mt7601u
        patch -p0 < ${srcdir}/vnd_reset.patch
}

build() {
        echo "Compiling module..."
        cd ${srcdir}/linux-${_pkgkernelver}/drivers/net/wireless/mediatek/mt7601u
        make -C /lib/modules/${_pkgcurkernver}/build/ KVER=${_pkgcurkernver} M=$(pwd) modules
}

package() {
        mkdir -p ${pkgdir}/usr/lib/modules/${_pkgcurkernver}/updates
        xz ${srcdir}/linux-${_pkgkernelver}/drivers/net/wireless/mediatek/mt7601u/mt7601u.ko
        cp ${srcdir}/linux-${_pkgkernelver}/drivers/net/wireless/mediatek/mt7601u/mt7601u.ko.xz ${pkgdir}/usr/lib/modules/${_pkgcurkernver}/updates
}
