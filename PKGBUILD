# Maintainer: Nice Aesthetics <nice(at)aesth(dot)dev>
_pkgbase=ek-loop-connect
pkgname=ek-loop-connect-dkms-git
pkgver=0.0.1
pkgrel=1
pkgdesc="Linux kernel hwmon driver for EK Loop Connect (DKMS, Git)"
arch=('x86_64')
url="https://github.com/pavelherr/ek-loop-connect"
license=('GPL2')
depends=('dkms')
provides=("${_pkgbase}" "${_pkgbase-dkms}")
conflicts=("${_pkgbase}" "${_pkgbase-dkms}")
install=${pkgname}.install
source=("$pkgname::git+${url}#branch=master"
        'dkms.conf')
sha256sums=('SKIP'
            '162e5e253190cdd61dd60105dc0f0cd3db858acb9db42c4bf8f47f5d22c9241f')

package() {
  # Copy dkms.conf
  install -Dm644 dkms.conf "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  # Set name and version
  sed -e "s/@_PKGBASE@/${_pkgbase}/" \
      -e "s/@PKGVER@/${pkgver}/" \
      -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  # Copy sources (including Makefile)
  cp -r "$srcdir/$pkgname/module"/* "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/
}
