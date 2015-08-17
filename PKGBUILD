# This PKGBUILD was created by (all credits go to) the following:
#  firefox-nightly maintainer: Cedric Mathieu
#  firefox-nightly contributor: coderoar
#  firefox-nightly contributor: cgirard
#  firefox-nightly contributor: Det
# A new nightly build is made every night with the latest patches, so force an update of this to have the very latest version.

# Warning(s):
#  Due to differences in code base, switching between versions while using the same profile is highly likely to corrupt said profile.

arch=('i686' 'x86_64')
license=('MPL')

pkgname=seamonkey-nightly-unstable
pkgdesc='SeaMonkey internet suite, unstable Trunk nightly build.'
url='http://www.seamonkey-project.org/dev/nightly'
conflicts=(seamonkey-nightly-stable)
#provides=()
#replaces=()
pkgver=2.18a1
pkgrel=1

source=('seamonkey-nightly.desktop' 'seamonkey-nightly-safe.desktop')
sha1sums=('27db57b20d3c97bd3aaf247930a1fc01e36c037f' 'c8a55ed37be1860419c084b21a191e275ebe06a0')
depends=('alsa-lib' 'dbus-glib' 'desktop-file-utils' 'fontconfig' 'gtk2>=2.11' 'hunspell' 'libevent' 'libnotify' 'libvpx' 'libxt' 'mime-types' 'mozilla-common' 'nss' 'pango>=1.14' 'sqlite' 'startup-notification')

package() {
	SX_SRC="seamonkey-${pkgver}.en-US.linux-${CARCH}.tar.bz2"
	SX_SRC_URI="http://ftp.mozilla.org/pub/mozilla.org/seamonkey/nightly/latest-comm-central-trunk/${SX_SRC}"

	msg "Downloading..."
	wget -N ${SX_SRC_URI}
	msg "Extracting..."
	bsdtar -x -f ${SX_SRC}
	msg "Packaging..."

#	uncomment this line to remove these
#	rm -rf seamonkey/{extensions,plugins,searchplugins}

	mkdir -p "${pkgdir}"/{usr/{bin,share/{applications,pixmaps}},opt}
	cp -r seamonkey "${pkgdir}/opt/seamonkey-${pkgver}"

	ln -s /opt/seamonkey-${pkgver}/seamonkey "${pkgdir}/usr/bin/seamonkey-nightly"
	install -m644 "${srcdir}"/{seamonkey-nightly.desktop,seamonkey-nightly-safe.desktop} "${pkgdir}/usr/share/applications/"
	install -m644 "${srcdir}/seamonkey/chrome/icons/default/seamonkey.png" "${pkgdir}/usr/share/pixmaps/${pkgname}-icon.png"
}