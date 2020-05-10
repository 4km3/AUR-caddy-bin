# Maintainer: pancho horrillo < pancho at pancho dot name >
# Maintainer: Rodrigo de la Fuente < rodrigo at delafuente dot email >
# Contributor: Christian Rebischke <chris.rebischke at archlinux dot org>
# Contributor: Maxime Borges < contact at maximeborg dot es >
# Contributor: Carl George < arch at cgtx dot us >

_name="caddy"
pkgname="$_name-bin"
pkgver=2.0.0
_distcommit='3b4be6c14bf1e519380853c31ec1d56112cf9451'
pkgrel=1
pkgdesc='Powerful, enterprise-ready, open source web server with automatic HTTPS written in Go'
arch=('x86_64' 'aarch64' 'armv7h')
url='https://caddyserver.com'
license=('Apache')
backup=("etc/$_name/Caddyfile")
provides=("$_name")
conflicts=("$_name")
install="$_name.install"

source=("https://github.com/caddyserver/$_name/releases/download/v$pkgver/${_name}_${pkgver}_checksums.txt"
	"https://raw.githubusercontent.com/caddyserver/dist/${_distcommit}/welcome/index.html"
	"$_name.conf::https://raw.githubusercontent.com/caddyserver/dist/${_distcommit}/archlinux/$_name.tmpfiles"
	"https://raw.githubusercontent.com/caddyserver/dist/${_distcommit}/archlinux/$_name.service"
	"https://raw.githubusercontent.com/caddyserver/dist/${_distcommit}/archlinux/Caddyfile")
source_x86_64=("https://github.com/caddyserver/$_name/releases/download/v$pkgver/${_name}_${pkgver}_linux_amd64.tar.gz")
source_aarch64=("https://github.com/caddyserver/$_name/releases/download/v$pkgver/${_name}_${pkgver}_linux_arm64.tar.gz")
source_armv7h=("https://github.com/caddyserver/$_name/releases/download/v$pkgver/${_name}_${pkgver}_linux_armv7.tar.gz")
sha256sums=('00150b4f8ac212644be54f8683b2f03248f216d2220021cfe341b9fb021fe733'
	    '19dfa250bdb962c50a49eb94706482c5c3d4ecd6df41f667a4bb5649d0490ce4'
	    'c8f002f5ba59985a643600dc3c871e18e110903aa945ef3f2da7c9edd39fbd7a'
	    'c0fbb270ee1094babebb84a3bbb029f61f9475fcd5ac84cbc8d9ef384c9765e7'
	    'f3919a12dd7ffe9b071e04e952a8ed3191c788ea42f103eac3e75d6819893279')
sha256sums_x86_64=('09562b68cf3e68718171613c4e2c06a43a5390180ed9e2a2bc38ba85bfc935f7')
sha256sums_aarch64=('ab9bcdaafddb71025542dc12e011e3a22d69582f14ff1a5a4ea87f5597c11e98')
sha256sums_armv7h=('7486ea3907ba6c10b48402fa715dce111d1907672128703ba63e6d38a52013e7')

prepare() {
	# Fix path to html dir
	sed -i 's|/var/www/html|/srv/http|g' index.html

	# Disable file_service
	sed -i 's|^file_server|# file_server|' Caddyfile
}

package() {
	install -Dm755 -t "$pkgdir/usr/bin"			"${_name}"
	install -Dm644 -t "$pkgdir/etc/$_name"			Caddyfile
	install -Dm644 -t "$pkgdir/usr/share/$_name"		index.html
	install -Dm644 -t "$pkgdir/usr/share/doc/$_name"	README.md
	install -Dm644 -t "$pkgdir/usr/lib/tmpfiles.d"		"$_name.conf"
	install -Dm644 -t "$pkgdir/usr/lib/systemd/system"	"$_name.service"
}
