# Maintainer: Carl George < arch at cgtx dot us >

_name="caddy"
pkgname="$_name-bin"
pkgver=0.10.10
pkgrel=1
pkgdesc='HTTP/2 web server with automatic HTTPS'
arch=('x86_64')
url='https://caddyserver.com'
license=('Apache')
backup=('etc/caddy/caddy.conf')
provides=("$_name")
conflicts=("$_name")
install='caddy.install'
source=("https://github.com/mholt/caddy/releases/download/v$pkgver/caddy_v${pkgver}_linux_amd64.tar.gz"
        'https://caddyserver.com/resources/images/brand/caddy-at-your-service-white.svg'
        'index.html'
        'caddy.service'
        'caddy.tmpfiles'
        'caddy.conf')
sha256sums=('28b10ecbfaf4a68ace9bc2cbc9f5382e81e35bc31a60cc096338ff43830d56ba'
            'e679dd79fd92dc351fc190c7af529c73e3896986aaa6b7c0ae01e561398d6b85'
            '6db7aec45e95bbbf770ce4d120a60d8e4992d2262a8ebf668521179279aa5ae7'
            '69e25def317a6172011472bd060655142f3085a0c81392f8a7a9c42b6a58bbd9'
            'bd4d912d083be176727882ccc1bbe577a27cc160db09238e5edc05ba458aebce'
            '38b0af1f02a8218b851febc09ebf52c3b570f0678688bbb3a48a744abf1ad266')

package() {
    install -D -m 0755 caddy "$pkgdir/usr/bin/caddy"
    install -D -m 0644 caddy-at-your-service-white.svg "$pkgdir/usr/share/caddy/caddy-at-your-service-white.svg"
    install -D -m 0644 index.html "$pkgdir/usr/share/caddy/index.html"
    install -D -m 0644 caddy.service "$pkgdir/usr/lib/systemd/system/caddy.service"
    install -D -m 0644 caddy.tmpfiles "$pkgdir/usr/lib/tmpfiles.d/caddy.conf"
    install -D -m 0644 caddy.conf "$pkgdir/etc/caddy/caddy.conf"
    install -d -m 0755 "$pkgdir/etc/caddy/conf.d"
}
