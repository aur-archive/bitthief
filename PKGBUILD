# Maintainer: David Becker <david dot becker at gmx dot org>
pkgname=bitthief
pkgver=0.5.0
pkgrel=2
pkgdesc='a free riding bittorrent client' 
arch=('i686' 'x86_64')
url="http://bitthief.ethz.ch/index.php"
license=('custom')
depends=('java-environment')
source=(http://bitthief.ethz.ch/dist/BitThief.jar)
md5sums=('700c54689899c23a3df41947cc3ee96c')

build() {

### start-script ###
echo -e "#!/usr/bin/env sh\nexec java -Xms192m -Xmx512m -jar /opt/"${pkgname}"/BitThief.jar $@" > ${pkgname}

### desktop-file ###
cat > ${pkgname}.desktop << "EOF"
[Desktop Entry]
Name=BitThief
GenericName=BitThief
Comment=free riding bittorrent client 
Terminal=false
Type=Application
Categories=Network;FileTransfer;P2P;
EOF
echo -e "Exec="${pkgname}"\nIcon="${pkgname}".png" >> ${pkgname}.desktop

}

package() {

install -d "${pkgdir}/usr/share/doc/${pkgname}/"
install -D -m644 "${srcdir}/LICENSE" "${pkgdir}/usr/share/doc/${pkgname}/LICENSE.html"

install -d "${pkgdir}/usr/share/applications/"
install -D -m644 "${srcdir}/${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"

install -d "${pkgdir}/usr/share/pixmaps/"
install -D -m644 "${srcdir}/bt_512.png" "${pkgdir}/usr/share/pixmaps/"${pkgname}".png"

install -d "${pkgdir}/opt/${pkgname}/"
install -D -m644 "BitThief.jar" "${pkgdir}/opt/${pkgname}/BitThief.jar"

install -d "${pkgdir}/usr/bin/"
install -D -m755 "${srcdir}/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
}
