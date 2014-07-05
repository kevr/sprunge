pkgname='sprunge'
pkgver='0.1.0'
pkgrel=1
pkgdesc='Upload data to sprunge.us via stdin'
license=('MIT')
url='https://github.com/kevr/sprunge'

arch=('i686' 'x86_64' 'armv6h')
depends=('python')
source=('sprunge')
sha256sums=('3e597f47a656ee7695dbad8f117a08cb3027aa67a503b2bbaccf4a77d555e1a7')

package()
{
    install -Dm755 "${srcdir}/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
}

