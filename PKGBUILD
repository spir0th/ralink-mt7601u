# Maintainer: Gian Borcillo <borcillofg2020@gmail.com>

_pkgbase=mt7601u
pkgname=ralink-mt7601u-dkms
pkgver=1.0.3
pkgrel=1
pkgdesc="DKMS module for MT7601u wireless adapter"
arch=('x86_64')
url="https://github.com/gianxddddd/linux-fixes"
license=('UNKNOWN')
depends=('dkms')
optdepends=('usb_modeswitch: To switch USB dongle mode from being a flash drive')
conflicts=("${_pkgbase}" "ralink-mt7601u" "mt7601u-ap-dkms" "mt7601u-firmware")
source=("https://cdn.discordapp.com/attachments/844193986254995456/971109113339711488/mt7601u.tar.gz"
        "dkms.conf")
sha256sums=("da4308f95b7ef059b3405d4570a2fa3cf393b18ade2e27987ac1157dda53efb2"
        "475226d9cb7cadea64527bf6f2f7f91b3d2baf408e6775131242141940a060c1")

package() {
        echo "Making source directories ..."
        cd ${pkgdir}
        mkdir -p ${pkgdir}/usr/src/${_pkgbase}-${pkgver}

        echo "Copying source files ..."
        cd ${pkgdir}
        cp -pr ${srcdir}/* ${pkgdir}/usr/src/${_pkgbase}-${pkgver}

        echo "Removing symlinks targeted to sources ..."
        rm ${pkgdir}/usr/src/${_pkgbase}-${pkgver}/${_pkgbase}.tar.gz

        echo "Configuring dkms.conf ..."
        sed -e "s/@_PKGBASE@/${_pkgbase}/" \
                -e "s/@PKGVER@/${pkgver}/" \
                -i ${pkgdir}/usr/src/${_pkgbase}-${pkgver}/dkms.conf
}
