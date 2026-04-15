# Maintainer: Xilin Wu <sophon@radxa.com>
# Upstream: https://github.com/linux-msm/hexagon-dsp-binaries

pkgbase=hexagon-dsp-binaries
pkgname=(
  hexagon-dsp-binaries
  hexagon-dsp-binaries-qualcomm-db820c
  hexagon-dsp-binaries-thundercomm-db845c
  hexagon-dsp-binaries-qualcomm-sdm845-hdk
  hexagon-dsp-binaries-thundercomm-rb5
  hexagon-dsp-binaries-thundercomm-rb1
  hexagon-dsp-binaries-thundercomm-rb2
  hexagon-dsp-binaries-thundercomm-rb3gen2
  hexagon-dsp-binaries-radxa-dragon-q6a
  hexagon-dsp-binaries-thundercomm-rubikpi3
  hexagon-dsp-binaries-qualcomm-sa8775p-ride
  hexagon-dsp-binaries-qualcomm-qcs8300-ride
  hexagon-dsp-binaries-qualcomm-qcs615-ride
  hexagon-dsp-binaries-qualcomm-hamoa-iot-evk
  hexagon-dsp-binaries-qualcomm-sm8750-mtp
  hexagon-dsp-binaries-qualcomm-kaanapali-mtp
  hexagon-dsp-binaries-qualcomm-glymur-crd
  hexagon-dsp-binaries-qualcomm-iq8275-evk
  hexagon-dsp-binaries-qualcomm-iq9075-evk
)
pkgver=20260410
pkgrel=2
pkgdesc="Hexagon DSP binaries and libraries for Qualcomm SoCs"
arch=('aarch64')
url="https://github.com/linux-msm/hexagon-dsp-binaries"
license=('MIT' 'LicenseRef-Qualcomm')
groups=('hexagon-dsp-binaries')
makedepends=('git')
options=('!strip' '!debug')
source=("${pkgbase}::git+https://github.com/linux-msm/hexagon-dsp-binaries.git#tag=${pkgver}")
sha256sums=('SKIP')

_dspdir=usr/share/qcom

build() {
  cd "$pkgbase"
  make install DESTDIR="$srcdir/_staging" prefix=/usr
}

_install_device() {
  cd "$srcdir/_staging"
  mkdir -p "$pkgdir/${_dspdir}/$(dirname "$1")"
  cp -a "${_dspdir}/$1" "$pkgdir/${_dspdir}/$1"
}

_install_licenses() {
  cd "$srcdir/$pkgbase"
  install -Dm644 LICENSE.MIT   "$pkgdir/usr/share/licenses/$1/LICENSE.MIT"
  install -Dm644 LICENSE.qcom  "$pkgdir/usr/share/licenses/$1/LICENSE.qcom"
  install -Dm644 LICENSE.qcom-2 "$pkgdir/usr/share/licenses/$1/LICENSE.qcom-2"
}

package_hexagon-dsp-binaries() {
  pkgdesc="Hexagon DSP binaries - machine configuration"
  depends=()
  optdepends=(
    'hexagon-dsp-binaries-qualcomm-db820c: DSP binaries for Qualcomm db820c'
    'hexagon-dsp-binaries-thundercomm-db845c: DSP binaries for Thundercomm db845c (RB3)'
    'hexagon-dsp-binaries-qualcomm-sdm845-hdk: DSP binaries for Qualcomm SDM845-HDK'
    'hexagon-dsp-binaries-thundercomm-rb5: DSP binaries for Thundercomm RB5'
    'hexagon-dsp-binaries-thundercomm-rb1: DSP binaries for Thundercomm RB1'
    'hexagon-dsp-binaries-thundercomm-rb2: DSP binaries for Thundercomm RB2'
    'hexagon-dsp-binaries-thundercomm-rb3gen2: DSP binaries for Thundercomm RB3gen2'
    'hexagon-dsp-binaries-radxa-dragon-q6a: DSP binaries for Radxa Dragon Q6A'
    'hexagon-dsp-binaries-thundercomm-rubikpi3: DSP binaries for Thundercomm RUBIK Pi 3'
    'hexagon-dsp-binaries-qualcomm-sa8775p-ride: DSP binaries for Qualcomm SA8775P-RIDE'
    'hexagon-dsp-binaries-qualcomm-qcs8300-ride: DSP binaries for Qualcomm QCS8300-RIDE'
    'hexagon-dsp-binaries-qualcomm-qcs615-ride: DSP binaries for Qualcomm QCS615-RIDE'
    'hexagon-dsp-binaries-qualcomm-hamoa-iot-evk: DSP binaries for Qualcomm Hamoa IoT EVK'
    'hexagon-dsp-binaries-qualcomm-sm8750-mtp: DSP binaries for Qualcomm SM8750-MTP'
    'hexagon-dsp-binaries-qualcomm-kaanapali-mtp: DSP binaries for Qualcomm Kaanapali-MTP'
    'hexagon-dsp-binaries-qualcomm-glymur-crd: DSP binaries for Qualcomm Glymur-CRD'
    'hexagon-dsp-binaries-qualcomm-iq8275-evk: DSP binaries for Qualcomm IQ8275-EVK'
    'hexagon-dsp-binaries-qualcomm-iq9075-evk: DSP binaries for Qualcomm IQ9075-EVK'
  )

  cd "$srcdir/_staging"
  mkdir -p "$pkgdir/${_dspdir}/conf.d/"
  install -Dm644 "${_dspdir}/conf.d/"*.yaml \
    "$pkgdir/${_dspdir}/conf.d/"
  _install_licenses "$pkgname"
}

# Dragonboard 820c
package_hexagon-dsp-binaries-qualcomm-db820c() {
  pkgdesc="Hexagon DSP binaries for Qualcomm db820c"
  _install_device "apq8096/Qualcomm/db820c"
  _install_licenses "$pkgname"
}

# Dragonboard 845c / RB3
package_hexagon-dsp-binaries-thundercomm-db845c() {
  pkgdesc="Hexagon DSP binaries for Thundercomm db845c (RB3)"
  _install_device "sdm845/Thundercomm/db845c"
  _install_licenses "$pkgname"
}

# SDM845 HDK (symlinks to db845c firmware)
package_hexagon-dsp-binaries-qualcomm-sdm845-hdk() {
  pkgdesc="Hexagon DSP binaries for Qualcomm SDM845-HDK"
  depends=('hexagon-dsp-binaries-thundercomm-db845c')
  _install_device "sdm845/Qualcomm/SDM845-HDK"
  _install_licenses "$pkgname"
}

# RB5
package_hexagon-dsp-binaries-thundercomm-rb5() {
  pkgdesc="Hexagon DSP binaries for Thundercomm RB5"
  _install_device "sm8250/Thundercomm/RB5"
  _install_licenses "$pkgname"
}

# RB1
package_hexagon-dsp-binaries-thundercomm-rb1() {
  pkgdesc="Hexagon DSP binaries for Thundercomm RB1"
  _install_device "qcm2290/Thundercomm/RB1"
  _install_licenses "$pkgname"
}

# RB2
package_hexagon-dsp-binaries-thundercomm-rb2() {
  pkgdesc="Hexagon DSP binaries for Thundercomm RB2"
  _install_device "qrb4210/Thundercomm/RB2"
  _install_licenses "$pkgname"
}

# RB3gen2
package_hexagon-dsp-binaries-thundercomm-rb3gen2() {
  pkgdesc="Hexagon DSP binaries for Thundercomm RB3gen2"
  _install_device "qcm6490/Thundercomm/RB3gen2"
  _install_licenses "$pkgname"
}

# Radxa Dragon Q6A
package_hexagon-dsp-binaries-radxa-dragon-q6a() {
  pkgdesc="Hexagon DSP binaries for Radxa Dragon Q6A"
  _install_device "qcs6490/radxa/dragon-q6a"
  _install_licenses "$pkgname"
}

# Thundercomm RUBIK Pi 3 (adsp is own firmware; cdsp symlinks to RB3gen2)
package_hexagon-dsp-binaries-thundercomm-rubikpi3() {
  pkgdesc="Hexagon DSP binaries for Thundercomm RUBIK Pi 3"
  depends=('hexagon-dsp-binaries-thundercomm-rb3gen2')
  _install_device "qcs6490/Thundercomm/RubikPi3"
  _install_licenses "$pkgname"
}

# SA8775P RIDE
package_hexagon-dsp-binaries-qualcomm-sa8775p-ride() {
  pkgdesc="Hexagon DSP binaries for Qualcomm SA8775P-RIDE"
  _install_device "sa8775p/Qualcomm/SA8775P-RIDE"
  _install_licenses "$pkgname"
}

# QCS8300 RIDE
package_hexagon-dsp-binaries-qualcomm-qcs8300-ride() {
  pkgdesc="Hexagon DSP binaries for Qualcomm QCS8300-RIDE"
  _install_device "qcs8300/Qualcomm/QCS8300-RIDE"
  _install_licenses "$pkgname"
}

# QCS615 RIDE
package_hexagon-dsp-binaries-qualcomm-qcs615-ride() {
  pkgdesc="Hexagon DSP binaries for Qualcomm QCS615-RIDE"
  _install_device "qcs615/Qualcomm/QCS615-RIDE"
  _install_licenses "$pkgname"
}

# Hamoa IoT EVK
package_hexagon-dsp-binaries-qualcomm-hamoa-iot-evk() {
  pkgdesc="Hexagon DSP binaries for Qualcomm Hamoa IoT EVK"
  _install_device "x1e80100/Qualcomm/Hamoa-IoT-EVK"
  _install_licenses "$pkgname"
}

# SM8750 MTP
package_hexagon-dsp-binaries-qualcomm-sm8750-mtp() {
  pkgdesc="Hexagon DSP binaries for Qualcomm SM8750-MTP"
  _install_device "sm8750/Qualcomm/SM8750-MTP"
  _install_licenses "$pkgname"
}

# Kaanapali MTP
package_hexagon-dsp-binaries-qualcomm-kaanapali-mtp() {
  pkgdesc="Hexagon DSP binaries for Qualcomm Kaanapali-MTP"
  _install_device "kaanapali/Qualcomm/Kaanapali-MTP"
  _install_licenses "$pkgname"
}

# Glymur CRD
package_hexagon-dsp-binaries-qualcomm-glymur-crd() {
  pkgdesc="Hexagon DSP binaries for Qualcomm Glymur-CRD"
  _install_device "glymur/Qualcomm/Glymur-CRD"
  _install_licenses "$pkgname"
}

# IQ8275 EVK (symlinks to QCS8300-RIDE firmware)
package_hexagon-dsp-binaries-qualcomm-iq8275-evk() {
  pkgdesc="Hexagon DSP binaries for Qualcomm IQ8275-EVK"
  depends=('hexagon-dsp-binaries-qualcomm-qcs8300-ride')
  _install_device "qcs8300/Qualcomm/IQ8275-EVK"
  _install_licenses "$pkgname"
}

# IQ9075 EVK (symlinks to SA8775P-RIDE firmware)
package_hexagon-dsp-binaries-qualcomm-iq9075-evk() {
  pkgdesc="Hexagon DSP binaries for Qualcomm IQ9075-EVK"
  depends=('hexagon-dsp-binaries-qualcomm-sa8775p-ride')
  _install_device "sa8775p/Qualcomm/IQ9075-EVK"
  _install_licenses "$pkgname"
}
